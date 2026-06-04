---
title: Implement streaming media services for Adobe Analytics or Customer Journey Analytics
description: Learn about the implementation paths for Adobe streaming media services.
uuid: null
feature: Streaming Media
role: User, Admin, Developer
exl-id: ed9297b1-6487-4099-bc62-0c3a40572255
TQID: https://experienceleague.adobe.com/aFrxbzBLlf1ngetaM-GsNFXz6TUXi6Pic3quLVI297c
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
  - id: df312454-73c4-43f6-a90e-18f5043f074c
    internal-label: Tags
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
# Implement streaming media services for Adobe Analytics or Customer Journey Analytics

There are various ways to implement Adobe streaming media services. For a detailed comparison of supported devices and platforms for the implementation methods described on this page, see [Supported devices and platforms](/help/getting-started/supported-devices.md).

## Edge implementation methods

Adobe recommends using Edge Network implementation methods for all new Adobe Analytics or Customer Journey Analytics customers.

* **Media for Edge Network SDK / Extension:** Collects data from the web, iOS and Android devices, or Roku devices and sends it to Edge Network. Data can then be sent either to Customer Journey Analytics or Adobe Analytics. 

  For more information about the Media for Edge Network SDK / Extension, see the [Edge implementation overview](/help/implementation/edge/overview.md).

* **Media Edge API:** Can be customized to collect data from any device or format (including, mobile, web, and over-the-top devices) and sends data to Edge Network. Data can then be sent either to Customer Journey Analytics or Adobe Analytics. 

  For more information about the Media Edge API, see [Media Edge API overview](https://developer.adobe.com/cja-apis/docs/endpoints/media-edge/).

![CJA workflow](assets/streaming-media-edge.png)

## Adobe Analytics-only implementation methods

The Edge implementation methods described above are recommended for both Customer Journey Analytics and Adobe Analytics, especially for new implementations.

In addition to the Edge implementation methods, other implementation methods are available. These implementation methods were designed for use with Adobe Analytics. However, existing customers with any of the following implementation methods can still make data available in Customer Journey Analytics by creating an [Analytics source connection](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/analytics.html).

Adobe Analytics-only implementation methods use the Adobe Analytics for Streaming Media Add-on. For prerequisites and a list of methods, see the [Analytics-only implementation overview](/help/implementation/analytics-only/overview.md).

* **Media Extension with tags:** The Adobe Media Analytics for Audio and Video extension provides the functionality for adding the Media tracker instance to a tags-enabled site or project. Data is sent to Adobe Analytics.

  For information on installing, configuring, and implementing the Media Extension with tags, see [Adobe Media Analytics (3.x SDK) for Audio and Video extension overview](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/media-analytics-3x/overview.html).

* **Media SDK:**  The Media SDK allows you to measure multiple media platforms, including websites, mobile phones, connected TVs, tablets, OTT devices, set-top boxes, and gaming consoles. (For more information, see [Supported devices and platforms](/help/getting-started/supported-devices.md).)

  The Media SDKs use the Media Collection APIs for tracking. Data is sent to Adobe Analytics.

  For information about downloading and installing Media SDKs and extensions, see [Get Media SDKs, Extensions using Tags, and OTT SDKs](/help/getting-started/download-sdks.md).

* **Media Collection APIs:** Because the Media Collection APIs are customizable, they can be used for applications that require custom tracking capabilities and for devices not supported by the Media SDKs. The Media Collection APIs track audio and video events using RESTful HTTP calls. Data is sent to Adobe Analytics.

  For information about using the Media Collection APIs, see [Media Collection APIs](media-collection-api/mc-api-overview.md).


![Analytics workflow](assets/analytics-implementation.png)
