---
title: Error
description: Signal that the media player encountered an error.
feature: Streaming Media
role: Developer
---

# Error

The error event signals that the media player encountered an error. Tracking an error does not close the session. If the error prevents playback from continuing, call [Session end](session/session-end.md) after the error event.

* **Prerequisites**: [Session start](session/session-start.md)
* **Associated metric**: [[!UICONTROL Error impacted streams]](/help/reporting/metrics/error-impacted-streams.md)

The `errorDetails.source` property accepts only two values: `player` (errors originating in the media player) and `external` (errors from an outside source such as a CDN or network).

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.error"` and the required `errorDetails`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.error",
    mediaCollection: {
      errorDetails: {
        name: "media-error-001",
        source: "player"
      },
      sessionID: "{sid}",
      playhead: 45
    }
  }
});
```

>[!TAB iOS]

Call `trackError` with an error ID string.

```swift
tracker.trackError(errorId: "media-error-001")
```

>[!TAB Android]

Call `trackError` with an error ID string.

```kotlin
tracker.trackError("media-error-001")
```

>[!TAB Roku]

Call `sendMediaEvent` with `eventType: "media.error"` and the required `errorDetails`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.error",
        "mediaCollection": {
            "errorDetails": {
                "name": "media-error-001",
                "source": "player"
            },
            "playhead": 45
        }
    }
})
```

>[!TAB Media Edge API]

Call the [error](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/error/) endpoint with the required `errorDetails`:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/error?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.error",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 45,
        "errorDetails": {
          "name": "media-error-001",
          "source": "player"
        }
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

Call `trackError` with an error ID string:

```javascript
tracker.trackError("media-error-001");
```

>[!TAB Chromecast]

Call `trackError` with an error ID string:

```javascript
ADBMobile.media.trackError("media-error-001");
```

>[!TAB Media Collection API]

Send an `error` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 45, "ts": 1699523820000 },
  "eventType": "error",
  "params": {
    "media.errorId": "media-error-001",
    "media.errorSource": "player"
  }
}
```

>[!ENDTABS]
