---
title: Learn How to Track Errors Using JavaScript 3.x
description: Learn about implementing error tracking using the Media SDK in browser apps (JS).
exl-id: 3769fc47-fbc4-4498-9d2a-04c88cdd0e83
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/Dd505O47PRpcQmSM82BIF1wXYWXxsZNNO8c97Qj9zl4
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Track errors using JavaScript 3.x{#track-errors-on-javascript}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing any previous versions of the SDK, you can download the Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Implement error tracking

1. Track media player errors:

    ```js
    onPlayerError = function() {
        tracker.trackError("errorId");
    };
    ```

>[!NOTE]
>
>Tracking media player errors will not stop the media tracking session. If the media player error prevents the playback from continuing, make sure that the media tracking session is closed by calling `trackSessionEnd` after calling `trackError`.
