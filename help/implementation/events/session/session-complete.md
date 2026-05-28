---
title: Session complete
description: Signal that the viewer reached the end of the main content.
feature: Streaming Media
role: Developer
---

# Session complete

The session complete event signals that the viewer reached the end of the main content. It does not immediately close the session; the session remains open until it expires naturally. If you want to immediately close the session, call [Session end](session-end.md) instead.

* **Prerequisites**: [Session start](session-start.md)
* **Associated metric**: [[!UICONTROL Content completes]](/help/reporting/metrics/content-completes.md)

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.sessionComplete"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionComplete",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 128
    }
  }
});
```

>[!TAB iOS]

Call `trackComplete` when the media player reaches the end of content.

```swift
tracker.trackComplete()
```

>[!TAB Android]

Call `trackComplete` when the media player reaches the end of content.

```kotlin
tracker.trackComplete()
```

>[!TAB Roku]

Call `sendMediaEvent` with `eventType: "media.sessionComplete"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.sessionComplete",
        "mediaCollection": {
            "playhead": 128
        }
    }
})
```

>[!TAB Media Edge API]

Call the [sessionComplete](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessioncomplete) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/sessionComplete?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.sessionComplete",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 128
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

Call `trackComplete` when the media player reaches the end of content:

```javascript
tracker.trackComplete();
```

>[!TAB Chromecast]

Call `trackComplete` when the media player reaches the end of content:

```javascript
ADBMobile.media.trackComplete();
```

>[!TAB Media Collection API]

Send a `sessionComplete` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 128, "ts": 1699523820000 },
  "eventType": "sessionComplete"
}
```

>[!ENDTABS]
