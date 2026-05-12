---
title: Test 2  Media Interruption
description: Learn about the media interruption test used in validation.
uuid: eeccd534-63fd-4dd3-b096-0431bc9a11ff
exl-id: 3f22ce2d-4385-4a3b-8d1f-52e25a9b1101
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/gVEDMjM05nDnzCB6l-9CjyUzoArcmyN4jgsjmjllRiY
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
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
  - id: e992d880-33bc-4949-a648-aa7d410276cd
    internal-label: Validation
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
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
---
# Test 2: Media Interruption{#test-media-interruption}

This test case validates mobile interruption behavior.

## Test procedure

You must complete and record these tasks in following order:

1. **Start the media player**

    When the media player starts, the following calls are sent in the following order:

    1. Adobe Analytics (AppMeasurement) Start
    1. Media Analytics (heartbeats) Start
    1. Media Analytics (heartbeats) Adobe Analytics Start call requested

    The first two calls above contain additional metadata and variables. For call parameters and metadata, see [Test call details.](/help/legacy/validation/test-call-details.md#start-the-media-player)

    The third call above tells the Media Analytics server that the Media SDK requested that the Adobe Analytics Start call (`pev2=ms_s`) be sent to the Adobe Analytics server.

1. **Play main content for at least 5 minutes uninterrupted**

    **Content Play**

    During content playback, the Media SDK sends play calls (heartbeats) to the Media Analytics server every ten seconds.

    For call parameters and metadata, see [Test call details.](/help/legacy/validation/test-call-details.md#play-main-content)

    Also see your platform's [Track Ads](/help/use-cases/track-ads/track-ads-overview.md) instructions for additional information about these Ad calls.

1. **Move app or browser to the background**

    While the app runs in the background, only `main:pause` calls should be sent to the Media Analytics server, starting with VHL version 1.6.6 and later.

1. **Bring app or browser back to foreground**

    On returning from background, content playback should resume.

1. **Play main content media for at least 5 minutes uninterrupted**

    For call parameters and metadata, see [Test Call Details.](/help/legacy/validation/test-call-details.md#play-main-content)

1. **Close media player**

    No additional tracking calls should fire after the media player is closed.
