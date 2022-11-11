---
title: Learn How To Track Seeking on iOS
description: Learn how to track Seek Start and Seek Complete events using the Media SDK on iOS.
uuid: 1d31ae99-384f-4b4d-b557-4018db177349
exl-id: e8cb4962-2a14-4bfe-9a25-2405e503ba0b
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Track seeking on iOS{#track-seeking-on-ios}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Seek tracking constants

|  Constant name  | Description&nbsp;&nbsp;&nbsp;&nbsp;  |
|---|---|
|  `ADBMediaHeartbeatEventSeekStart`  | Constant for tracking Seek Start event.  |
|  `ADBMediaHeartbeatEventSeekComplete`  | Constant for tracking Seek Complete event.  |

## Implement seeking

1. Listen for the playback seeking events from the media player, and on seek start event notification, track seeking using the `SeekStart` event:

    ```
    - (void)onSeekStart:(NSNotification *)notification {
        [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventSeekStart  
                         mediaObject:nil  
                         data:nil];
    }
    ```

1. On seek complete notification from the media player, track the end of seeking using the `SeekComplete` event:

    ```
    - (void)onSeekComplete:(NSNotification *)notification {
        [_mediaHeartbeat trackEvent:ADBMediaHeartbeatEventSeekComplete  
                         mediaObject:nil  
                         data:nil];
    }
    ```

See the tracking scenario [VOD playback with seeking in the main content](/help/use-cases/tracking-scenarios/vod-seeking.md) for more information.
