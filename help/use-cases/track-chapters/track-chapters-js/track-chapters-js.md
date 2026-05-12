---
title: Learn to Track Chapters and Segments Using JavaScript 2.x
description: Learn about implementing chapter and segment tracking using the Media SDK in browser apps (JS).
uuid: ef99edf7-7a77-46c4-8429-bc9a856b98d6
exl-id: 9964ec0c-cce9-4ccc-bd26-a2b3fcdc3e28
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/o-swyVIDTLtvNcst3f1hPsZfJdAhamMDT3WYd1-WNx0
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
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
# Track chapters and segments using JavaScript 2.x{#track-chapters-and-segments-on-javascript}

The following instructions provide guidance for implementation using 2.x SDKs.

>[!IMPORTANT]
>
> If you are implementing a 1.x version of the SDK, you can download the Developers Guide here: [Download SDKs.](/help/getting-started/download-sdks.md)

1. Identify when the chapter start event occurs and create the `ChapterObject` instance by using the chapter information.

    `ChapterObject` chapter tracking reference:  

    >[!NOTE]
    >
    >These variables are only required if you are planning to track chapters.

    | Variable Name | Description | Required |
    | --- | --- | :---: |
    | `name` | Chapter name | Yes |
    | `position` | Chapter position | Yes |
    | `length` | Chapter length | Yes |
    | `startTime` | Chapter start time | Yes |

    Chapter object:

    ```js
    var chapterInfo =  
      MediaHeartbeat.createChapterObject(<CHAPTER_NAME>,  
                                         <POSITION>,  
                                         <LENGTH>,  
                                         <START_TIME>);
    ```

1. If you include custom metadata for the chapter, create the context data variables for the metadata:

    ```js
    var chapterCustomMetadata = {
        segmentType: "Sample segment type",  
        segmentName: "Sample segment name",  
        segmentInfo: "Sample segment info"
    };
    ```

1. To begin tracking the chapter playback, call the `ChapterStart` event in the `MediaHeartbeat` instance:

    ```js
    _onChapterStart = function() {
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterStart,  
                                        chapterObject,  
                                        chapterCustomMetadata);
    };
    ```

1. When playback reaches the chapter end boundary, as defined by your custom code, call the `ChapterComplete` event in the `MediaHeartbeat` instance:

    ```js
    _onChapterComplete = function() {
       this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterComplete);
    };
    ```

1. If chapter playback did not complete because the user chose to skip the chapter (for example, if the user seeks out of the chapter boundary), call the `ChapterSkip` event in the MediaHeartbeat instance:

    ```js
    _onChapterSkip = function() {
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.ChapterSkip);
    };
    ```

1. If there are any additional chapters, repeat steps 1 through 5.
