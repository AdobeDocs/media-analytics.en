---
title: Migration Overview
description: Learn about migrating from 1.x to 2.x versions of the Media SDK.
uuid: d84f55bc-fa90-45c1-b97d-cb5fe58e80c0
exl-id: b3b8b9f8-a6e9-4ed1-85c1-80e61460e8a0
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/mM6vZFyx6BG5MZXrzOc5hkBM6pOdzBCLiSL3WgON9LU
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
  - id: c8add8f2-4250-4fd9-9cde-9707036c567d
    internal-label: Methods
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Legacy Migration Overview for VHL 1.x to VHL 2.x {#migration-overview}

The migration from VHL 1.x to VHL 2.x is straightforward, with the new version featuring simplified APIs for initialization, configuration, and player delegates.i

Here are the primary differences between 1.x and 2.x:

* **Plugins, Delegates -** You no longer need to implement plugins and delegates for Analytics, VideoPlayer, and Heartbeat.
* **Configuration -** You no longer need to instantiate configurations for the 1.x plugins.

## Benefits of 2.x {#benefits-of-two-x}

* All of the public methods are consolidated into the `MediaHeartbeat` class to make implementation easier on developers.
* All configs are now consolidated into the `MediaHeartbeatConfig` class.
* You no longer need to instantiate configs for the Analytics, VideoPlayer, and Heartbeat plugins. You only need to instantiate the `MediaHeartbeat` class with `MediaHeartbeatDelegate` and `MediaHeartbeatConfig` instances. This is the only implementation that is required to initialize Media Analytics.

   With the initialization of `MediaHeartbeat`, you can safely delete all of the implementation for Analytics Plugin, VideoPlayer Plugin, and Heartbeat Plugin. Also, remove all the existing implementation for initialization that takes in an array of plugins as an input. You can see side-by-side comparisons of the 1.x and 2.x implementations here: [Code comparison: 1.x to 2.x.](./code-comparison-1x-2x.md)

The new APIs in 2.x are described in detail here: [API 1.x to 2.x conversion.](./1x-2x-api-change.md)
