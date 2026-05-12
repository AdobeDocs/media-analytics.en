---
title: What Streaming Media Implementation Paths are Available?
description: Learn about Adobe Streaming Media implementation paths including Adobe Experience Platform Data Collection.
exl-id: eee70e62-ba45-440a-8ce1-e151b66d2c1f
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/U9PBQc7dHNmONZc06t1Xi7EITkveGUkzcst6Sakqqzo
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7
    internal-label: Integrations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
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
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Implementation paths {#implementation-paths}

**THIS CONTENT WAS MOVED TO THE CURRENT IMPLEMENTATION PATHS FILE**

For each implementation path, customers need to contact their Sales Representative or Adobe Account Team to sign a new Sales Order as Customer Journey Analytics Streaming Media Collection and Adobe Analytics for Streaming Media has a unique SKU and changes from a pricing model based on server calls to a model based on video streams.

## Adobe Experience Platform Data Collection with the Adobe Media Analytics extension

>[!NOTE]
>Adobe Experience Platform Launch has been rebranded as a suite of data collection technologies in Experience Platform. Several terminology changes have rolled out across the product documentation as a result. Please refer to the following [document](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=en) for a consolidated reference of the terminology changes.


Tags in Adobe Experience Platform are the next generation of tag management capabilities from Adobe. Tags give customers a simple way to deploy and manage all of the analytics, marketing, and advertising tags necessary to power relevant customer experiences. Tags are offered to Adobe Experience Cloud customers as an included value-add feature.

Tags empower anyone to build and maintain their own integrations, called extensions. These extensions are available to Adobe Experience Cloud customers in an app-store experience so they can quickly install, configure, and deploy their tags.

An extension is a package of code (JavaScript, HTML, and CSS) that extends the tags functionality. Build, manage, and update your integrations using a virtually self-service interface. You can think of extensions as apps you use to achieve your tasks.For more information, see the *Tags overview* article in the [Adobe Experience Platform Documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)

The Adobe Media Analytics (MA) extension adds the core JavaScript Media SDK (Media 2.x SDK) for audio and video. This extension provides the functionality for adding the `MediaHeartbeat` tracker instance to a Data Collection site or project.

Adobe Data Collection with the Media Analytics extension requires the following:
* You must be an Adobe Experience Cloud customer.
* You must deploy Data Collection or DTM embed code on your web pages.
* [Analytics Extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html)
* [Experience Cloud ID Extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/id-service/overview.html)


## Client Side

These are Media Analytics-only integrations. You can choose Video Heartbeat SDK and/or the Media Collection API integrations. This path can be used across any video player, including customer and/or OVP players such as Brightcove, Ooyala, thePlatform, and so on.

If Media Analytics is your intended path, see the [Media SDK Implementation](/help/legacy/setup/legacy-setup-overview.md) and the [Media Collection API.](/help/implementation/media-collection-api/mc-api-overview.md)

>[!IMPORTANT]
>To use Media Analytics, customers must also use Adobe Analytics.

## Adobe Primetime

Adobe Primetime is an Adobe Experience Cloud solution that helps content programmers and distributors monetize media on every connected screen.

Primetime eliminates the complexity of reaching, monetizing, and activating global audiences across devices by providing a modular platform for video publishing, advertising, personalization, and analytics. Additionally, Primetime offers solutions and value around the following:

* Support for accurately measuring Linear and VOD content types.
* Support for measuring ad breaks with (or without) dynamic ad insertion.
* TVSDK's seamless ad insertion model allows for analytics that directly measures the ad playback, which increases accuracy.
* Robust set of events and metadata to ensure accuracy across QoS buffering or mobile connectivity interruptions issues and end-user interactions such as seeking, pausing, and backgrounding on mobile.
* Integrated support for Nielsen DTVR (linear) with ID3 metadata and DCR with CMS metadata.


TVSDK is already integrated with the Media Analtyics (Heartbeats) SDK, which makes implementation much easier and faster across every supported platform. To leverage Primetime, follow the same guidelines and prerequisites found in [Client-side](/help/legacy/intro-to-ava/implementation-paths/client-side-path.md) along with the following docs for your platform(s): [Primetime User Guide.](https://helpx.adobe.com/primetime/user-guide.html)

   You should also contact your Sales Representative/Account Manger to discuss what you need to do to purchase TVSDK.
