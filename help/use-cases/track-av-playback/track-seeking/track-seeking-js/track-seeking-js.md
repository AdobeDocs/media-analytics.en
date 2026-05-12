---
title: Learn How To Track Seeking using JavaScript 2.x
description: Learn how to track Seek Start and Seek Complete events using the Media SDK in browser apps (JS 2.x).
uuid: 089947fb-8bae-4ae8-b215-53793620efd7
exl-id: 90f35376-24d8-405d-82b4-d6b737acf7b9
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/wQkUvm0BhqYGd9q-k2YKe2f0kkhjkM3hpwDYuAIw3QU
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
# Track seeking using JavaScript 2.x{#track-seeking-on-javascript}

The following instructions provide guidance for implementation across all 2.x SDKs. 

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Seek tracking constants

|  Constant name  | Description&nbsp;&nbsp;&nbsp;&nbsp;  |
|---|---|
|  `SeekStart`  | Constant for tracking Seek Start event.  |
|  `SeekComplete`  | Constant for tracking Seek Complete event.  |

## Implement seeking

1. Listen for the playback seeking events from the media player, and on seek start event notification, track seeking using the `SeekStart` event:

    ```js
    _onSeekStart = function() {
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekStart);
    };
    ```

1. On seek complete notification from the media player, track the end of seeking using the `SeekComplete` event:

    ```js
    _onSeekComplete = function() {
        this._mediaHeartbeat.trackEvent(MediaHeartbeat.Event.SeekComplete);
    };
    ```

See the tracking scenario [VOD playback with seeking in the main content](/help/use-cases/tracking-scenarios/vod-seeking.md) for more information.
