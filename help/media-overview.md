---
title: Adobe streaming media overview
description: Use Adobe Streaming Media solutions to gain powerful insight for content, audio, and advertisements.
uuid: b3cbe240-b94d-42b8-a99c-0280334aaa14
exl-id: 826530f7-2c39-41ef-b3b4-d3f44b46858f
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/EJ6osO9PkXBubSF7a7HebRJhpSTamNnghofASOs7E-E
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
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
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
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
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
    internal-label: Customer engagement
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# Adobe streaming media services overview

![Banner](./assets/media_analytics_banner.png)

Adobe streaming media services provide powerful collection, measurement, and personalization tools for streaming media content, such as audio, video, and advertisement for streaming media providers. You can combine streaming media metrics with capabilities such as Audience Analytics, Mobile, or Cross-Device Analytics. 

Streaming media data easily integrates into the following Adobe Experience Platform products:

* Adobe Analytics

* Customer Journey Analytics

* Adobe Journey Optimizer

* Real-Time Customer Data Platform 

>[!IMPORTANT]
>
>To implement the streaming media services, contact your Adobe Sales Representative or Adobe Account Team to make sure the Customer Journey Analytics Streaming Media Collection Add-on or the Adobe Analytics for Streaming Media Add-on is part of your product portfolio.

## Key features

The benefits of the streaming media services include real-time monitoring, detailed analysis, actionable insights, monetization opportunities, and more.

* **Real-time analysis**: Make real-time, actionable decisions utilizing key performance metrics such as media starts, across multiple channels.

  With the streaming media services, you get near real-time, granular details of duration, stops, and starts that let you evaluate and combine video and audio metrics. These insights allow you to understand your customers' viewing and listening habits and increase engagement with highly personalized recommendations.

* **Drive engagement**: Fully engage users through fewer buffering events and by understanding where and when ads should play within content to provide a smooth, less intrusive experience that delivers repeat visits.

* **Holistic picture**: Combine multiple data points across all of your content distributors to get a full view of all your media activity. Measure engagement and views/listens across all possible channels.

  Streaming media services enable you to track the full customer journey across your site and streaming apps to visualize the customer path and interests and to provide enhanced recommendations and personalize customer experiences.  Media measurement allows you to categorize your data into multiple dimensions and segments, capturing all of the metadata you need to do a complete and detailed analysis. You can then analyze data and attribute success criteria to fully consumed media, average time spent, and completed ads.

* **Vital metrics**: Measure vital delivery metrics related to Quality of Experience (QoE) such as dropped frames, time spent buffering, and average bitrate. 

* **Increased granularity**: Evaluate viewing behavior at the most granular level, including individual visitor time of day, concurrent viewers or listeners by minute, and average duration the content was consumed.

* **Precise measurement**: Measure across the multiple devices used for media consumption, including OTT, smartphone, tablet, desktop, and more, to monitor user engagement patterns and habits.

* **Segmentation**: Apply classifications to your players, devices, genres, chapters, and shows to see how each has an impact on your overall views/listens and customer engagement with content, audio, ads, and combined.


## How it works

Streaming media services tracking data is collected from a player using the Media for Edge Network SDK/Extension, Media Extension with Tags, Media SDKs, Media Edge API, or the Media Collection API. 

All granular data (up to 10 seconds) is sent either to the Media Analytics Service or Experience Edge (depending on the [implementation method](/help/implementation/overview.md) you choose), which collect and process the data for each individual playback session. 

After a playback session ends, the computed tracking data is sent either to Adobe Analytics or Customer Journey Analytics for storage and reporting. 

>[!NOTE]
>
>With Customer Journey Analytics implementations, data can be sent to Customer Journey Analytics either using Experience Edge or using the Analytics Data Connector (ADC).


For detailed information about the various implementation methods, see [Implement streaming media services for Adobe Analytics or Customer Journey Analytics](/help/implementation/overview.md).
