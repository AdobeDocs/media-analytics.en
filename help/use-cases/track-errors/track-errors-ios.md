---
title: Learn How to Track Errors on iOS
description: Learn about implementing error tracking using the Media SDK on iOS.
uuid: 18ea93d3-5948-4375-bcdb-72309268e38d
exl-id: c4ce7092-a102-41da-80a6-a4359f925708
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Track errors on iOS{#track-errors-on-ios}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Implement error tracking

1. Track media player errors:

    ```
    - (void)onPlayerError:(NSNotification *)notification {
        [_mediaHeartbeat trackError:@"mediaoErrorId"];
    }
    ```

>[!NOTE]
>
>Tracking media player errors will not stop the media tracking session. If the media player error prevents the playback from continuing, make sure that the media tracking session is closed by calling `trackSessionEnd` after calling `trackError`.
