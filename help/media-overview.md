---
title: Adobe Analytics for Streaming Media Overview
description: Use Streaming Media Analytics to gain powerful insight for content, audio, and advertisements.
uuid: b3cbe240-b94d-42b8-a99c-0280334aaa14
exl-id: 826530f7-2c39-41ef-b3b4-d3f44b46858f
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Adobe Analytics for Streaming Media overview

![Banner](./assets/media_analytics_banner.png)

Adobe Analytics for Streaming Media provides powerful measurement tools for audio, video, and advertisements. You can combine Streaming Media metrics with other Adobe Analytics capabilities, such as Audience Analytics, Mobile, or Cross-Device Analytics. 

Streaming Media can be purchased as an add-on to Adobe Analytics<!-- update this when SKUs are available for other AEP products -->, and Streaming Media metrics easily integrate into the following Adobe Experience Platform products:

* Adobe Analytics

* Customer Journey Analytics

* Adobe Journey Optimizer

* Real-Time Customer Data Platform 

>[!IMPORTANT]
>
>To implement Adobe Analytics Streaming Media, contact your Adobe Sales Representative or Adobe Account Team to make sure Streaming Media is part of your product portfolio.

## Key features

The benefits of Adobe Analytics for Streaming Media include real-time monitoring, detailed analysis, actionable insights, monetization opportunities, and more.

* **Real-time analysis**: Make real-time, actionable decisions utilizing key performance metrics such as media starts, across multiple channels.

  With Analytics for Streaming Media, you get near real-time, granular details of duration, stops, and starts that let you evaluate and combine video and audio metrics. These insights allow you to understand your customers' viewing and listening habits and increase engagement with highly personalized recommendations.

* **Drive engagement**: Fully engage users through fewer buffering events and by understanding where and when ads should play within content to provide a smooth, less intrusive experience that delivers repeat visits.

* **Holistic picture**: Combine multiple data points across all of your content distributors to get a full view of all your media activity. Measure engagement and views/listens across all possible channels.

  Adobe Analytics for Streaming Media enables you to track the full customer journey across your site and streaming apps to visualize the customer path and interests and to provide enhanced recommendations and personalize customer experiences.  Media measurement allows you to categorize your data into multiple dimensions and segments, capturing all of the metadata you need to do a complete and detailed analysis. You can then analyze data and attribute success criteria to fully consumed media, average time spent, and completed ads.

* **Vital metrics**: Measure vital delivery metrics related to Quality of Experience (QoE) such as dropped frames, time spent buffering, and average bitrate. 

* **Increased granularity**: Evaluate viewing behavior at the most granular level, including individual visitor time of day, concurrent viewers or listeners by minute, and average duration the content was consumed.

* **Precise measurement**: Measure across the multiple devices used for media consumption, including OTT, smartphone, tablet, desktop, and more, to monitor user engagement patterns and habits.

* **Segmentation**: Apply classifications to your players, devices, genres, chapters, and shows to see how each has an impact on your overall views/listens and customer engagement with content, audio, ads, and combined.


## How it works

Streaming media tracking data is collected from a player using the Media for Edge Network SDK/Extension, Media Extension with Tags, Media SDKs, Media Edge API, or the Media Collection API. 

All granular data (up to 10 seconds) is sent either to the Media Analytics Service or Experience Edge (depending on the [implementation method](/help/implementation/overview.md) you choose), which collect and process the data for each individual playback session. 

After a playback session ends, the computed tracking data is sent either to Adobe Analytics or Customer Journey Analytics for storage and reporting. 

>[!NOTE]
>
>With Customer Journey Analytics implementations, data can be sent to Customer Journey Analytics either using Experience Edge or using the Analytics Data Connector (ADC).


For detailed information about the various implementation methods, see [Implement Streaming Media for Adobe Analytics or Customer Journey Analytics](/help/implementation/overview.md).
