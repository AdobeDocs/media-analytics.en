---
title: Prerequisites for Adobe Analytics-only implementations
description: Learn About Prerequisites for using the Streaming Media Collection with Adobe Analytics-only implementations or Edge implementations
feature: Streaming Media, Workspace Basics
role: User, Admin, Developer
exl-id: 7b042e45-e35a-43d6-b59e-282573c6a326
TQID: https://experienceleague.adobe.com/OqimGafihuirpnAaZ4AvrX2lrOmCtr0FLXk3QwoVTew
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
  - id: c77ba355-6681-41fe-b719-563d3f507fdb
    internal-label: Mobile SDK
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
# Prerequisites for Edge implementations

The prerequisites described in this section are specific to implementing the Adobe Streaming Media Collection with Edge implementations.

1. **Complete the general prerequisites**<br>
Whether you implement the Streaming Media Collection for Adobe Analytics-only implementations or for Edge implementations, ensure that you meet the [general prerequisites](/help/getting-started/prereqs.md).

1. **Confirm that you're implementing an Adobe solution compatible with Edge Network and the Streaming Media Collection**<br>
When implementing the Streaming Media Collection with Edge, you must also have a working Customer Journey Analytics, Adobe Analytics, Adobe Journey Optimizer, or a Real-Time Customer Data Platform implementation. See the following documentation resources for more information:
   * [Customer Journey Analytics guide](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-landing.html?lang=en)
   * [Implement Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html) 
   * [Adobe Journey Optimizer documentation](https://experienceleague.adobe.com/docs/journey-optimizer.html)
   * [Real-Time Customer Data Platform documentation](https://experienceleague.adobe.com/docs/real-time-customer-data-platform.html)

1. **Obtain the media tracking server URL**<br>
Ask your Customer Journey Analytics Representative for the media tracking server URL. <!-- This is the `collection-api-server` URL for the Mobile SDK, the JavaScript SDK, and the non-collection-api tracking server for Roku. Domain names for API implementation is: `[your_namespace].hb-api.omtrdc.net`. -->

1. **Implement the Streaming Media Collection using the Edge Network**<br>
Follow the steps in [Implement the Streaming Media Collection using the Edge Network](/help/implementation/edge/implementation-edge.md).
