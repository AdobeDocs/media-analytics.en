---
title: Learn How to Track Chapters and Segments on Roku
description: Learn about implementing chapter and segment tracking using the Media SDK on Roku.
uuid: 15c07131-77d7-4a97-92c6-0a190c6b08d3
exl-id: b5eb8be7-4b85-4ba7-9216-dd691be7ba46
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/Z06I7x3nDZvYHoQHo9bcjs4UiS2YR6yN8rwJqG3vX1w
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
# Track chapters and segments on Roku{#track-chapters-and-segments-on-roku}

The following instructions provide guidance for implementation using 2.x SDKs.

>[!IMPORTANT]
>
> If you are implementing a 1.x version of the SDK, you can download the Developers Guide here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Implement standard ad metadata

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

    ```
    chapterInfo =  
      adb_media_init_chapterinfo(<CHAPTER_NAME>,  
                                 <POSITION>,  
                                 <LENGTH>,  
                                 <START_TIME>);)
    ```

1. If you include custom metadata for the chapter, create the context data variables for the metadata:

    ```
    chapterContextData = {}
    chapterContextData["seg_type"] = "seg_type"
    chapterContextData["seg_name"] = "seg_name"
    chapterContextData["seg_info"] = "seg_info"
    ```

1. To begin tracking the chapter playback, call the `ChapterStart` event in the `MediaHeartbeat` instance:

    ```
    ADBMobile().mediaTrackEvent(MEDIA_CHAPTER_START, chapterInfo, chapterContextData)
    ```

1. When playback reaches the chapter end boundary, as defined by your custom code, call the `ChapterComplete` event in the `MediaHeartbeat` instance.

    ```
    chapterContextData = {}
    ADBMobile().mediaTrackEvent(MEDIA_CHAPTER_COMPLETE, chapterInfo, chapterContextData)
    ```

1. If chapter playback did not complete because the user chose to skip the chapter (for example, if the user seeks out of the chapter boundary), call the `ChapterSkip` event in the MediaHeartbeat instance.

    ```
    chapterContextData = {}
    ADBMobile().mediaTrackEvent(MEDIA_CHAPTER_SKIP, chapterInfo, chapterContextData)
    ```

1. If there are any additional chapters, repeat steps 1 through 5.
