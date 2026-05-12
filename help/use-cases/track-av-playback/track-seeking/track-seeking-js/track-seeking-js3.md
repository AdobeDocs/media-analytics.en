---
title: Learn How To Track Seeking using JavaScript 3.x
description: Learn how to track Seek Start and Seek Complete events using the Media SDK in browser apps (JS 3.x).
exl-id: b7152436-520e-4f38-a8ad-1027ca3f1f6c
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/orl8i3mc3iQm3t8cY9yCLOmFDoAHiryvMMANvfs5wpM
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Track seeking using JavaScript 3.x{#track-seeking-on-javascript}

The following instructions provide guidance for implementation across all 3.x SDKs.

>[!IMPORTANT]
>
>If you are implementing any previous versions of the SDK, you can download the Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Seek tracking constants

|  Constant name  | Description&nbsp;&nbsp;&nbsp;&nbsp;  |
|---|---|
|  `SeekStart`  | Constant for tracking Seek Start event.  |
|  `SeekComplete`  | Constant for tracking Seek Complete event.  |

## Implement seeking

1. Listen for the playback seeking events from the media player, and on seek start event notification, track seeking using the `SeekStart` event:

    ```js
    _onSeekStart = function() {
        tracker.trackEvent(ADB.Media.Event.SeekStart);
    };
    ```

1. On seek complete notification from the media player, track the end of seeking using the `SeekComplete` event:

    ```js
    _onSeekComplete = function() {
        tracker.trackEvent(ADB.Media.Event.SeekComplete);
    };
    ```

See the tracking scenario [VOD playback with seeking in the main content](/help/use-cases/tracking-scenarios/vod-seeking.md) for more information.
