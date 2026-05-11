---
title: Chapter offset
description: Set the offset of the chapter inside the content, in seconds from the start.
feature: Streaming Media
role: Developer
---

# Chapter offset

>[!BEGINSHADEBOX]

*This page covers data collection for the **Chapter offset** variable. See [Chapter offset](/help/reporting/variables/dimensions/chapter-offset.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The chapter offset variable is the offset of the chapter inside the content, measured in seconds from the start. The first chapter typically has offset `0`; subsequent chapters have offsets matching their playhead start time.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.chapter.offset` |
| **XDM collection field** | [`mediaCollection.chapterDetails.offset`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-collection) |
| **Required** | No (Mobile SDK); Yes (Edge, Media Collection API) |
| **Sent with** | Chapter start, chapter close |

## Web SDK

Set `offset` inside `mediaCollection.chapterDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.chapterStart",
    mediaCollection: {
      chapterDetails: {
        friendlyName: "Act II",
        index: 2,
        offset: 240,
        length: 360
      },
      sessionID: "{sid}",
      playhead: 240
    }
  }
});
```

## Mobile SDK

Pass the offset in seconds as the fourth argument (`startTime`) to `createChapterObject`.

**iOS (Swift)**

```swift
let chapterObject = Media.createChapterObjectWith(name: "Act II",
                                              position: 2,
                                                length: 360,
                                             startTime: 240)

tracker.trackEvent(event: MediaEvent.ChapterStart, info: chapterObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val chapterObject = Media.createChapterObject("Act II",
                                              2L,
                                              360.0,
                                              240.0)

tracker.trackEvent(Media.Event.ChapterStart, chapterObject, null)
```

## Roku (BrightScript)

Set `offset` inside `mediaCollection.chapterDetails` when calling `sendMediaEvent` for `media.chapterStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.chapterStart",
        "mediaCollection": {
            "chapterDetails": {
                "friendlyName": "Act II",
                "index": 2,
                "offset": 240,
                "length": 360
            },
            "playhead": 240
        }
    }
})
```

## Media Edge API

Call the [chapterStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/chapters/#chapterstart) endpoint with `offset` inside `mediaCollection.chapterDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.chapterStart",
      "mediaCollection": {
        "chapterDetails": {
          "index": 2,
          "offset": 240,
          "length": 360
        },
        "sessionID": "{sid}",
        "playhead": 240
      }
    }
  }]
}
```

## Media SDK

Pass the offset as the fourth argument to `ADB.Media.createChapterObject`:

```javascript
var chapterInfo = ADB.Media.createChapterObject(
  "Act II",
  2,
  360,
  240
);

tracker.trackEvent(ADB.Media.Event.ChapterStart, chapterInfo, contextData);
```

## Media Collection API

Include `media.chapter.offset` in the `params` object of your `chapterStart` POST request:

```json
{
  "playerTime": { "playhead": 240, "ts": 1699523820000 },
  "eventType": "chapterStart",
  "params": {
    "media.chapter.offset": 240
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
