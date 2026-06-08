---
title: Play
description: Signal that the media player entered the playing state.
feature: Streaming Media
role: Developer
---

# Play

The play event signals that the media player changed state to playing. Send it on the initial start of content, on autoplay, and whenever the player resumes after a pause or buffer. There is no separate resume event; a play event after [Pause start](pause-start.md) or [Buffer start](buffer-start.md) serves as the resume.

* **Prerequisites**: [Session start](../session/session-start.md)
* **Associated metric**: [[!UICONTROL Content starts]](/help/reporting/metrics/content-starts.md)

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.play"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.play",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

>[!TAB iOS]

Call `trackPlay` when the media player begins or resumes playback.

```swift
tracker.trackPlay()
```

>[!TAB Android]

Call `trackPlay` when the media player begins or resumes playback.

```kotlin
tracker.trackPlay()
```

>[!TAB Roku Edge]

Call `sendMediaEvent` with `eventType: "media.play"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.play",
        "mediaCollection": {
            "playhead": 0
        }
    }
})
```

>[!TAB Media Edge API]

Call the [play](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/play/) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/play?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.play",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 0
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Call `trackPlay` when the media player begins or resumes playback:

```javascript
tracker.trackPlay();
```

>[!TAB Chromecast]

Call `trackPlay` when the media player begins or resumes playback:

```javascript
ADBMobile.media.trackPlay();
```

>[!TAB Roku 2.x]

Call `mediaTrackPlay` when the media player begins or resumes playback:

```brightscript
ADBMobile().mediaTrackPlay()
```

>[!TAB Media Collection API]

Send a `play` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "play"
}
```

>[!ENDTABS]
