---
title: Learn to Track Chapters and Segments Using JavaScript 3.x
description: Learn about implementing chapter and segment tracking using the Media SDK in browser apps (JS).
exl-id: 00ba11df-d226-45a2-a561-dc9f15dcf714
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/YZAcZVcqS15hCae-LYwjpSYztXijauQNIzElCcWcPT0
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
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
# Track chapters and segments using JavaScript 3.x{#track-chapters-and-segments-on-javascript}

The following instructions provide guidance for implementation using 3.x SDKs.

>[!IMPORTANT]
>
> If you are implementing any previous versions of the SDK, you can download the Developers Guide here: [Download SDKs.](/help/getting-started/download-sdks.md)

1. Identify when the chapter start event occurs and create the `ChapterObject` instance by using the chapter information.

    `ChapterObject` chapter tracking reference:

    >[!NOTE]
    >
    >These variables are only required if you are planning to track chapters.

    | Variable Name | Type | Description |
    | --- | --- | --- |
    | `name` | string | Non empty string denoting chapter name. |
    | `position` | number | The position of the chapter within the content, starting with 1. |
    | `length` | number | Positive number denoting length of the chapter. |
    | `startTime` | number | Playhead value at start of chapter. |

    Chapter object:

    ```js
    var chapterObject =
      ADB.Media.createChapterObject.createChapterObject(<CHAPTER_NAME>,
                                         <POSITION>,
                                         <LENGTH>,
                                         <START_TIME>);
    ```

1. If you include custom metadata for the chapter, create the context data variables for the metadata:

    ```js
    var chapterMetadata = {};
    chapterMetadata["segmentType"] = "Sample segment type";
    ```

1. To begin tracking the chapter playback, call the `ChapterStart` event in the `MediaHeartbeat` instance:

    ```js
    _onChapterStart = function() {
      tracker.trackEvent(ADB.Media.Event.ChapterStart, chapterObject, chapterMetadata);

    };
    ```

1. When playback reaches the chapter end boundary, as defined by your custom code, call the `ChapterComplete` event in the `MediaHeartbeat` instance:

    ```js
    _onChapterComplete = function() {
       tracker.trackEvent(ADB.Media.Event.ChapterComplete);
    };
    ```

1. If chapter playback did not complete because the user chose to skip the chapter (for example, if the user seeks out of the chapter boundary), call the `ChapterSkip` event in the MediaHeartbeat instance:

    ```js
    _onChapterSkip = function() {
        tracker.trackEvent(ADB.Media.Event.ChapterSkip);
    };
    ```

1. If there are any additional chapters, repeat steps 1 through 5.
