---
title: How to set up a mobile SDK using Tags for Streaming Media Services
description: Learn how to implement Adobe streaming media services for mobile apps.
feature: Streaming Media
role: User, Admin, Developer
exl-id: b4944b5f-cbae-4efc-9ef7-962d3f342240
TQID: https://experienceleague.adobe.com/IfnXB76Qycsic-ezOzZX4X-5RakbTQ0tlt7va6q2fZ8
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
# Install Mobile SDKs {#install-mobile-sdks}

>[!IMPORTANT]
>
>This page covers the Analytics-only Mobile SDK implementation. For the recommended implementation, see [Implement Streaming Media using the Edge Network](/help/implementation/edge/edge-mobile-sdk.md).

To implement Adobe streaming media services for mobile apps on Android or iOS, install and configure the following:

*   **Adobe Experience Platform Mobile SDK**

    To collect data, use either of the following:
    * Tags in Adobe Experience Platform. Tags in Adobe Experience Platform is a tag management solution that lets you deploy Analytics code alongside other tagging requirements.
    * Adobe Experience Platform Edge

*   **Media SDK for Android** or **Media SDK for iOS**

*   **Adobe Media Analytics for Audio and Video extension**

To download the SDKs and for additional documentation resources, see [Get Media SDKs, Extensions using Tags, and OTT SDKs](/help/getting-started/download-sdks.md)

*   **Obtain valid configuration parameters**

    These parameters can be obtained from an Adobe representative after you set up your analytics account.

*   **Include the following APIs in your media player**

    * *An API to subscribe to player events* - The Media SDK requires that you call a set of simple APIs when events occur in your player.

    * *An API that provides player information* - This includes information about currently playing such as the media name, play head position, ads, or chapter.
