---
title: Learn How to Track Errors on iOS
description: Learn about implementing error tracking using the Media SDK on iOS.
uuid: 18ea93d3-5948-4375-bcdb-72309268e38d
exl-id: c4ce7092-a102-41da-80a6-a4359f925708
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/EOLvyCedoFoK4cOm9oM7-bqHJW6793mMvZPx7MMXZCQ
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
