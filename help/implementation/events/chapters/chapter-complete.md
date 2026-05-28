---
title: Chapter complete
description: Signal that a chapter segment finished playing.
feature: Streaming Media
role: Developer
---

# Chapter complete

The chapter complete event signals that a chapter finished playing. Send it when the viewer reaches the end of a chapter. If the viewer skips the chapter, send [Chapter skip](chapter-skip.md) instead.

* **Prerequisites**: [Session start](../session/session-start.md), [Chapter start](chapter-start.md)
* **Associated metric**: [[!UICONTROL Chapter completes]](/help/reporting/metrics/chapter-completes.md)

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.chapterComplete"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.chapterComplete",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 240
    }
  }
});
```

>[!TAB iOS]

Call `trackEvent` with the `ChapterComplete` event type.

```swift
tracker.trackEvent(event: MediaEvent.ChapterComplete, info: nil, metadata: nil)
```

>[!TAB Android]

Call `trackEvent` with the `ChapterComplete` event type.

```kotlin
tracker.trackEvent(Media.Event.ChapterComplete, null, null)
```

>[!TAB Roku]

Call `sendMediaEvent` with `eventType: "media.chapterComplete"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.chapterComplete",
        "mediaCollection": {
            "playhead": 240
        }
    }
})
```

>[!TAB Media Edge API]

Call the [chapterComplete](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/chapters/#chaptercomplete) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/chapterComplete?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.chapterComplete",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 240
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

Call `trackEvent` with the `ChapterComplete` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.ChapterComplete, null, null);
```

>[!TAB Chromecast]

Call `trackEvent` with the `ChapterComplete` event type:

```javascript
ADBMobile.media.trackEvent(ADBMobile.media.Event.ChapterComplete);
```

>[!TAB Media Collection API]

Send a `chapterComplete` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 240, "ts": 1699523820000 },
  "eventType": "chapterComplete"
}
```

>[!ENDTABS]
