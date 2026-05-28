---
title: Chapter length
description: Set the length of each chapter, in seconds.
feature: Streaming Media
role: Developer
---

# Chapter length

>[!BEGINSHADEBOX]

*This page covers data collection for the **Chapter length** variable. See [Chapter length](/help/reporting/dimensions/chapter-length.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The chapter length variable is the duration of the chapter, in seconds. Set it on every `media.chapterStart` event.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.chapter.length` |
| **XDM collection field** | [`xdm.mediaCollection.chapterDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.chapter.length` |
| **Required** | No (Mobile SDK); Yes (Edge, Media Collection API) |
| **Sent with** | [Chapter start](/help/implementation/events/chapters/chapter-start.md), chapter close |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `length` inside `xdm.mediaCollection.chapterDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.chapterStart",
    mediaCollection: {
      chapterDetails: {
        friendlyName: "Pilot Episode - Opening",
        index: 1,
        offset: 0,
        length: 240
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

>[!TAB iOS]

Pass the chapter length in seconds as the third argument to `createChapterObject`.

```swift
let chapterObject = Media.createChapterObjectWith(name: "Pilot Episode - Opening",
                                              position: 1,
                                                length: 240,
                                             startTime: 0)

tracker.trackEvent(event: MediaEvent.ChapterStart, info: chapterObject, metadata: nil)
```

>[!TAB Android]

Pass the chapter length in seconds as the third argument to `createChapterObject`.

```kotlin
val chapterObject = Media.createChapterObject("Pilot Episode - Opening",
                                              1L,
                                              240.0,
                                              0.0)

tracker.trackEvent(Media.Event.ChapterStart, chapterObject, null)
```

>[!TAB Roku]

Set `length` inside `xdm.mediaCollection.chapterDetails` when calling `sendMediaEvent` for `media.chapterStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.chapterStart",
        "mediaCollection": {
            "chapterDetails": {
                "friendlyName": "Pilot Episode - Opening",
                "index": 1,
                "offset": 0,
                "length": 240
            },
            "playhead": 0
        }
    }
})
```

>[!TAB Media Edge API]

Call the [chapterStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/chapters/#chapterstart) endpoint with `length` inside `xdm.mediaCollection.chapterDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.chapterStart",
      "mediaCollection": {
        "chapterDetails": {
          "index": 1,
          "offset": 0,
          "length": 240
        },
        "sessionID": "{sid}",
        "playhead": 0
      }
    }
  }]
}
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Pass the chapter length as the third argument to `ADB.Media.createChapterObject`:

```javascript
var chapterInfo = ADB.Media.createChapterObject(
  "Pilot Episode - Opening",
  1,
  240,
  0
);

tracker.trackEvent(ADB.Media.Event.ChapterStart, chapterInfo, contextData);
```

>[!TAB Chromecast]

Pass the chapter length in seconds as the third argument (`length`) to `ADBMobile.media.createChapterObject`:

```javascript
var chapterInfo = ADBMobile.media.createChapterObject(
  "Pilot Episode - Opening",  // name
  1,                          // position
  240,                        // length (seconds)
  0                           // startTime
);
ADBMobile.media.trackEvent(ADBMobile.media.Event.ChapterStart, chapterInfo, null);
```

>[!TAB Media Collection API]

Include `media.chapter.length` in the `params` object of your `chapterStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "chapterStart",
  "params": {
    "media.chapter.length": 240
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
