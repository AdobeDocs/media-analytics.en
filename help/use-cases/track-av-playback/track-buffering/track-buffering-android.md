---
title: Learn How To Track Buffering on Android
description: Learn how to track buffering events on Android.
uuid: f16ce76d-1db3-4b51-8c98-54cb781f71d7
exl-id: fcea2ef8-53c5-41fb-8b70-06599c2d9cbf
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Track buffering on Android{#track-buffering-on-android}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDks.](/help/getting-started/download-sdks.md)

## Buffer tracking constants

|  Constant name  | Description&nbsp;&nbsp;&nbsp;&nbsp;  |
|---|---|
|  `MediaHeartbeat.Event.BufferStart`  | Constant for tracking Buffer Start event  |
|  `MediaHeartbeat.Event.BufferComplete`  | Constant for tracking Buffer Complete event  |

## Implement buffering

1. Listen for the playback buffering events from media player, and on buffer start event notification, track buffering using the `BufferStart` event:

   ```java
   public void onBufferStart(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.BufferStart, null, null);
   }
   ```

1. On buffer complete notification from the media player, track the end of buffering using the `BufferComplete` event:

   ```java
   public void onBufferComplete(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.BufferComplete,null, null);
   }
   ```

See the tracking scenario [VOD playback with buffering](/help/use-cases/tracking-scenarios/vod-buffering.md) for more information.
