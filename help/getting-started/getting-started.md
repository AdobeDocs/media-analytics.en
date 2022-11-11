---
title: Getting Started
description: Get started with Adobe Analytics for Streaming Media.
uuid:
feature: Media Analytics
role: User, Admin, Data Engineer
---

# Getting Started {#getting-started}

Adobe Analytics for Streaming Media offers two main implementation methods, the Media SDKs and the Media Collection APIs.

![methods](assets/getting-started2.png)

Using the built-in logic of the **Media SDKs**, you can accurately measure multiple media platforms, including websites, mobile phones, connected TVs, tablets, OTT devices, set-top boxes, and gaming consoles. You can even measure downloaded content. The insights you get go deep into user viewing engagement, so you can understand how long, when, and where viewers engage. The Media SDKs use the **Media Collection APIs** for tracking. The Media Collection APIs are customizable---if your application requires custom tracking capabilities. For devices not supported by the Media SDKs, you can use the Media Collection APIs.

The Adobe Analytics Streaming Media solution is provided for the following media platforms:

* Web
* Mobile
* Over-the-top
* Any connected device that could be used for streaming media or a server-to-server integration

For more information, see [Supported Devices and Platforms](#_Supported_devices_and).

>[!IMPORTANT]
>
>To implement Adobe Analytics Streaming Media, contact your Adobe Sales Representative or Account Manager to make sure Streaming Media is part of your product portfolio.

## Media SDKs for Streaming Media {#media-sdks}

Media SDKs for Streaming Media are available for JavaScript, Android, iOS, tvOS, Chromecast, and Roku platforms.

For information about downloading and installing Media SDKs, see [Get Media SDKs, Extensions using Tags, and OTT SDKs](/help/getting-started/download-sdks.md).


## Media Collection APIs {#media-collection-apis}

The **Media Collection APIs** allow you to customize your media analytics implementation. Use the Media Collection APIs to directly call Adobe's servers to perform almost any action that you can perform using the SDKs and more. Customize your data collection to create reports that explore, get insights, or answer important questions about your streaming media data.

For information about using the Media Collection APIs, see [Steaming Media API documentation](/help/implementation/media-collection-api/mc-api-overview.md).

## Adobe Extensions {#adobe-extensions}

>[!NOTE]
>
>NEED INTRO FOR THE EXTENSIONS

* The [**Adobe Media Analytics for Audio and Video extension**](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics/overview.html?lang=en) (Media Analytics extension), is required for iOS and tvOS implementations. It provides the functionality for adding the tracker instance to a tag site or project. The MA extension also requires the Analytics Extension and the Experience Cloud ID Extension.

* [Analytics Extension v1.6 or higher](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html?lang=en)—This extension allows you to load the Adobe Experience Platform Web SDK Javascript library to send data to Adobe solutions.

* [Experience Cloud ID Extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/id-service/overview.html?lang=en)—This extension implements the Experience Cloud ID Service which identifies visitors across all Experience Cloud solutions. The Experience Cloud ID Service is a personalization extension in Adobe Experience Platform.
