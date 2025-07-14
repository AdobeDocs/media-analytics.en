---
title: Prerequisites for Adobe Analytics-only implementations
description: Learn About Prerequisites for using the Streaming Media Collection with Adobe Analytics-only implementations or Edge implementations
feature: Streaming Media, System Requirements
role: User, Admin, Data Engineer
exl-id: 7b042e45-e35a-43d6-b59e-282573c6a326
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
