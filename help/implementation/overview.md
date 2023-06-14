---
title: Implement Streaming Media for Adobe Analytics or Customer Journey Analytics
description: Learn about Streaming Media implementation paths.
uuid: null
feature: Media Analytics
role: User, Admin, Data Engineer
exl-id: ed9297b1-6487-4099-bc62-0c3a40572255
---
# Implement Streaming Media for Adobe Analytics or Customer Journey Analytics

There are various ways to implement Streaming Media. New customers should use one of the recommended implementation methods. 

For a detailed comparison of supported devices and platforms for the implementation methods described on this page, see [Supported devices and platforms](/help/getting-started/supported-devices.md).

## Recommended implementation methods

The following implementation methods are recommended for all new Adobe Analytics or Customer Journey Analytics (CJA) customers:

* **Media for Edge Network SDK / Extension:** Collects data from iOS and Android devices and sends it to Edge. Data can then be sent either to CJA or Adobe Analytics. 

  For more information about the Media for Edge Network SDK / Extention, see [Install Media Analytics with Experience Platform Edge](/help/implementation/implementation-edge.md).

  >[!NOTE]
  >
  >This implementation method does not currently support the Web SDK.

* **Media Edge API:** Can be customized to collect data from any device or format (including, mobile, web, and over-the-top devices) and sends data to Edge. Data can then be sent either to CJA or Adobe Analytics. 

  <!-- For more information about the Media Edge API, see (link to John's docs when they're ready) -->

## Traditional implementation methods

Many existing customers use one of the following implementation methods, because these were the only implementation methods available before Experience Platform Edge was supported for Streaming Media. These implementation methods are no longer recommended for new CJA or Adobe Analytics customers. 

Existing customers with these implementation methods can still make data available in CJA by creating an [Analytics source connection](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/analytics.html).

* **Media Extension with tags:** The Adobe Media Analytics for Audio and Video extension provides the functionality for adding the Media tracker instance to a tags-enabled site or project. Data is sent to Adobe Analytics.

  For information on installing, configuring, and implementing the Media Extension with tags, see [Adobe Media Analytics (3.x SDK) for Audio and Video extension overview](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/media-analytics-3x/overview.html).

* **Media SDK:**  Data is sent to Adobe Analytics.

  For information about downloading and installing Media SDKs and extensions, see [Get Media SDKs, Extensions using Tags, and OTT SDKs](/help/getting-started/download-sdks.md).

* **Media Collection API:** Track audio and video events using RESTful HTTP calls. Data is sent to Adobe Analytics.

  For information about using the Media Collection APIs, see [Media Collection APIs](media-collection-api/mc-api-overview.md).




## Recommendations

**New customers:** Use Experience Edge. Even though the Web SDK is not yet supported with Experience Edge, we recommend that all new customers implement Streaming Media with Experience Edge. This allows for an easy migration

**Existing customers

The implementation path you follow depends on whether you choose to use the built-in logic of the Media SDKs (the standard, recommended implementation) or whether you choose to roll-your-own and use the simple—yet powerful and customizable Media Collection APIs (RESTful).

Choose the implementation path depending on the supported platforms. Some players are not supported by the Media SDKs or the Adobe Experience Platform Media Extensions. The Media Collection APIs provide a way to support those players. For information on supported devices, see [Supported devices and platforms](/help/getting-started/supported-devices.md).

![Media Flow](media-sdk/assets/choose-media-flow2.png)
