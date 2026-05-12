---
title: Learn How to Track Chapters and Segments on iOS
description: Learn about implementing chapter and segment tracking using the Media SDK on iOS.
uuid: ffc5ce9f-04ba-4059-92d4-4cb4180ac9ed
exl-id: ea8a1dd6-043f-41a4-9cef-845da92bfa32
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/xo94BYsFdo612h-FjNYkreRsjLC3lMYLXW-w-ltLkIE
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
# Track chapters and segments on iOS{#track-chapters-and-segments-on-ios}

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

    ```
    id chapterObject =  
      [ADBMediaHeartbeat createChapterObjectWithName:[CHAPTER_NAME]
                         position:[POSITION]
                         length:[LENGTH]
                         startTime:[START_TIME]];
    ```

1. If you include custom metadata for the chapter, create the context data variables for the metadata:

    ```
    NSMutableDictionary *chapterDictionary = [[NSMutableDictionary alloc] init];
    [chapterDictionary setObject:@"Sample segment type" forKey:@"segmentType"];
    [chapterDictionary setObject:@"Sample segment name" forKey:@"segmentName"];
    [chapterDictionary setObject:@"Sample segment info" forKey:@"segmentInfo"];
    ```

1. To begin tracking the chapter playback, call the `ChapterStart` event in the `MediaHeartbeat` instance:

    ```
    - (void)onChapterStart:(NSNotification *)notification {
        [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventChapterStart  
                         mediaObject:chapterObject     
                         data:chapterDictionary];
    }
    ```

1. When playback reaches the chapter end boundary, as defined by your custom code, call the `ChapterComplete` event in the `MediaHeartbeat` instance:

    ```
    - (void)onChapterComplete:(NSNotification *)notification {
        [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventChapterComplete  
                         mediaObject:nil  
                         data:nil];
    }
    ```

1. If chapter playback did not complete because the user chose to skip the chapter (for example, if the user seeks out of the chapter boundary), call the `ChapterSkip` event in the MediaHeartbeat instance:

    ```
    - (void)onChapterSkip:(NSNotification *)notification {
        [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventChapterSkip  
                         mediaObject:nil  
                         data:nil];
    }
    ```

1. If there are any additional chapters, repeat steps 1 through 5.
