---
title: Play
description: Signal that the media player entered the playing state.
feature: Streaming Media
role: Developer
---

# Play

The play event signals that the media player changed state to playing. Send it on the initial start of content, on autoplay, and whenever the player resumes after a pause or buffer. There is no separate resume event; a play event after [Pause start](pause-start.md) or [Buffer start](buffer-start.md) serves as the resume.

| Property | Value |
| --- | --- |
| **Prerequisites** | [Session start](../session/session-start.md) |
| **Associated metric** | [Content starts](/help/reporting/metrics/content-starts.md) |

## Web SDK

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

## Mobile SDK

Call `trackPlay` when the media player begins or resumes playback.

**iOS (Swift)**

```swift
tracker.trackPlay()
```

**Android (Kotlin)**

```kotlin
tracker.trackPlay()
```

## Roku (BrightScript)

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

## Media Edge API

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

## Media SDK

Call `trackPlay` when the media player begins or resumes playback:

```javascript
tracker.trackPlay();
```

## Media Collection API

Send a `play` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "play"
}
```
