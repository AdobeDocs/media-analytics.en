---
title: Learn How To Track Buffering Using JavaScript 3.x
description: Learn how to track buffering events in browser apps (JS).
exl-id: c6941942-02f9-4f9c-99ad-0c52ed2f793b
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Track buffering using JavaScript 3.x{#track-buffering-on-javascript}

The following instructions provide guidance for implementation across all 3.x SDKs. 

>[!IMPORTANT]
>
>If you are implementing any previous versions of the SDK, you can download the Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Buffer tracking constants

|  Constant name  | Description&nbsp;&nbsp;&nbsp;&nbsp;  |
|---|---|
|  `BufferStart`  | Constant for tracking Buffer Start event  |
|  `BufferComplete`  | Constant for tracking Buffer Complete event  |

## Implement buffering

1. Listen for the playback buffering events from media player, and on buffer start event notification, track buffering using the `BufferStart` event.

   ```js
   _onBufferStart = function() {
       tracker.trackEvent(ADB.Media.Event.BufferStart);
   };
   ```

1. On buffer complete notification from the media player, track the end of buffering using the `BufferComplete` event.

   ```js
   _onBufferComplete = function() {
       tracker.trackEvent(ADB.Media.Event.BufferComplete);
   };
   ```

See the tracking scenario [VOD playback with buffering](/help/use-cases/tracking-scenarios/vod-buffering.md) for more information.
