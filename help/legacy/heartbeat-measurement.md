---
title: About heartbeat measurement
description: Learn how heartbeats are used to collect video metrics.
feature: Media Analytics
role: User, Admin, Data Engineer
exl-id: 180dd9b1-877a-4ec1-8e81-c293800069c0
---
# About Heartbeat Measurement

Adobe Analytics uses "heartbeats" to collect video metrics. During video playback, heartbeats are sent to the heartbeat tracking server to measure time played. The heartbeat calls are sent every ten seconds. Heartbeats result in granular video engagement metrics and more accurate video fallout reports. Adobe Analytics for Streaming Media measures heartbeats using Adobe Launch with the Media Analytics extension, the Media SDK and the Media Collection API. The `AppMeasurement` and `VisitorID` components are used to receive video data.

Using heartbeats Adobe Analytics for Streaming Media provide the following benefits:

| Feature | Description |
|---|---|
| Media Events | Detailed and Custom Events are sent every 10 seconds for main content and every 1 second for ads |
| Metrics and Dimensions | Clear standardized metrics, dimensions, and benchmarks across vendors. With a standardized solution across all platforms, you can use consistent, standardized variables across all of your media and platforms to allow for a more efficient cross-campaign, device and vendor comparison. |
| Integrations | Experience Cloud ID is linked to Adobe Experience Cloud for easier cross-analysis. With automatic Adobe Experience Cloud integration, you can segment your media audiences, target them, and make media recommendations based on user preferences. |
| Pricing | Transparent tracking by media stream (single) |
| Implementation and Support | Streamlined configuration with ongoing updates and improvements. With a streamlined implementation process, you can quickly map variables through your player API and validate implementations using the Adobe Debug Tool to ensure all necessary variables are tracked accurately. |
| Partner Sharing | Federated Analytics and Certified Metrics. With shared data through Federated Analytics, you can capitalize on our industry-first media sharing capabilities, to evaluate data holistically across all of your media distribution partners—operators, programmers, and distributors. |
| Advanced Tracking | Downloaded Content Tracking, Error Recovery Tracking and Concurrent Viewers. You can track streaming media content that is downloaded and played on a device regardless of its connectivity. |
