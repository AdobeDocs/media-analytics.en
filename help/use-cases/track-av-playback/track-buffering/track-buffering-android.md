---
title: Learn How To Track Buffering on Android
description: Learn how to track buffering events on Android.
uuid: f16ce76d-1db3-4b51-8c98-54cb781f71d7
exl-id: fcea2ef8-53c5-41fb-8b70-06599c2d9cbf
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/7TnD-Kk0PprXOoNELRMz9N9-sbbVQdh1FQyfQfC6xlI
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
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
