---
title: Learn How to Track Chapters and Segments Explained
description: How to implement chapter and segment tracking with the Media SDK.
uuid: 3fe32425-5e2a-4886-8fea-d91d15671bb0
exl-id: d213b633-be3b-4eb8-be71-0ef55e78a570
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/PAadkD9nJ7IRf7LdsNzIWtFp0yv54x0xV-Js-ona0Lg
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Overview{#overview}

The following instructions provide guidance for implementation using 2.x SDKs.

>[!IMPORTANT]
> 
> If you are implementing a 1.x version of the SDK, you can download the Developers Guide here: [Download SDKs.](/help/getting-started/download-sdks.md)

Chapter and segment tracking is available for custom-defined media chapters or segments. Some common uses for chapter tracking are to define custom segments based on media content (such as baseball innings), or to define content segments between ad breaks. Chapter tracking is **not** required for core media tracking implementations.

Chapter tracking includes chapter starts, chapter completes, and chapter skips. You can use the media player API with customized segmentation logic to identify chapter events and to populate the required and optional chapter variables.

## Player events

### On chapter start

* Create the chapter object instance for the chapter, `chapterObject`
* Populate the chapter metadata, `chapterCustomMetadata`
* Call `trackEvent(MediaHeartbeat.Event.ChapterStart, chapterObject, chapterCustomMetadata);`

### On chapter complete

* Call `trackEvent(MediaHeartbeat.Event.ChapterComplete);`

### On chapter skip

* Call `trackEvent(MediaHeartbeat.Event.ChapterSkip);`

## Implement chapter tracking {#implement-chapter-tracking}

1. Identify when the chapter start event occurs and create the `ChapterObject` instance by using the chapter information.

    Here is the `ChapterObject` chapter tracking reference:  

    >[!NOTE]
    >
    >These variables are only required if you are planning to track chapters.

    | Variable Name | Description | Required |
    | --- | --- | :---: |
    | `name` | Chapter name | Yes |
    | `position` | Chapter position | Yes |
    | `length` | Chapter length | Yes |
    | `startTime` | Chapter start time | Yes |

1. If you include custom metadata for the chapter, create the context data variables for the metadata.
1. To begin tracking the chapter playback, call the `ChapterStart` event in the `MediaHeartbeat` instance.
1. When playback reaches the chapter end boundary, as defined by your custom code, call the `ChapterComplete` event in the `MediaHeartbeat` instance.
1. If chapter playback did not complete because the user chose to skip the chapter (for example, if the user seeks out of the chapter boundary), call the `ChapterSkip` event in the MediaHeartbeat instance.
1. If there are any additional chapters, repeat steps 1 through 5.

The following sample code uses the JavaScript 2.x SDK for an HTML5 media player. You should use this code with the core media playback code.

```js
/* Call on chapter start */
if (e.type == "chapter start") {
    var chapterObject = MediaHeartbeat.createChapterObject("Inning 5",5,500,2500);
    /* Set custom context data*/
    var chapterCustomMetadata = {
        segmentType:"Baseball Innings",
        segmentName:"Inning 5",
        segmentInfo:"Game Six"
    }
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart,  
                                   chapterObject,  
                                   chapterCustomMetadata);
};

/* Call on chapter complete */
if (e.type == "chapter complete") {
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterComplete);
};

/* Call on chapter skip */
if (e.type == "chapter skip") {
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip);
};
```
