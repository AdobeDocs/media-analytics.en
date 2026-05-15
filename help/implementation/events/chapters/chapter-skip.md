---
title: Chapter skip
description: Signal that the viewer skipped a chapter.
feature: Streaming Media
role: Developer
---

# Chapter skip

The chapter skip event signals that the viewer skipped a chapter before it finished. Send it when the viewer navigates past the chapter boundary without watching it to completion. Send [Chapter complete](chapter-complete.md) if the chapter plays to its end.

* **Prerequisites**: [Session start](../session/session-start.md), [Chapter start](chapter-start.md)
* **Associated metric**: None

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.chapterSkip"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.chapterSkip",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 60
    }
  }
});
```

## Mobile SDK

Call `trackEvent` with the `ChapterSkip` event type.

**iOS (Swift)**

```swift
tracker.trackEvent(event: MediaEvent.ChapterSkip, info: nil, metadata: nil)
```

**Android (Kotlin)**

```kotlin
tracker.trackEvent(Media.Event.ChapterSkip, null, null)
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.chapterSkip"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.chapterSkip",
        "mediaCollection": {
            "playhead": 60
        }
    }
})
```

## Media Edge API

Call the [chapterSkip](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/chapters/#chapterskip) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/chapterSkip?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.chapterSkip",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 60
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Call `trackEvent` with the `ChapterSkip` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.ChapterSkip, null, null);
```

## Media Collection API

Send a `chapterSkip` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 60, "ts": 1699523820000 },
  "eventType": "chapterSkip"
}
```
