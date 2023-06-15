---
title: How to set up a mobile SDK using Tags for Streaming Media
description: Learn how to implement Adobe Streaming Media for mobile apps.
feature: Media Analytics
role: User, Admin, Data Engineer
exl-id: b4944b5f-cbae-4efc-9ef7-962d3f342240
---
# Install Mobile SDKs {#install-mobile-sdks}

To implement streaming media for mobile apps on Android or iOS, install and configure the following:

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
