---
title: Learn How to Track Errors on Android
description: Learn about implementing error tracking using the Media SDK on Android.
uuid: 7d0c77e5-924c-4619-8e29-3484748ab736
exl-id: 6c4f693d-45c0-4a9c-bda1-c8721afe31f5
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Track errors on Android{#track-errors-on-android}

The following instructions provide guidance for implementation using 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

1. Track media player errors:

    ```java
    public void onPlayerError(Observable observable, Object data) {  
        _heartbeat.trackError("mediaErrorID");
    }
    ```

>[!NOTE]
>
>Tracking media player errors will not stop the media tracking session. If the media player error prevents the playback from continuing, make sure that the media tracking session is closed by calling `trackSessionEnd` after calling `trackError`.
