---
title: About heartbeat measurement
description: Learn how heartbeats are used to collect video metrics.
feature: Streaming Media
role: User, Admin, Developer
exl-id: 180dd9b1-877a-4ec1-8e81-c293800069c0
TQID: https://experienceleague.adobe.com/t6Y8Nj7WaEP76UOj8cCp40zSc3mHMfZuC9j5CifVIOg
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7
    internal-label: Integrations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
  - id: e6c28e30-8689-4bf4-8fa8-561343d308a9
    internal-label: Experience Cloud integration
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
---
# About Heartbeat Measurement

Adobe streaming media services use "heartbeats" to collect video metrics. During video playback, heartbeats are sent to the heartbeat tracking server to measure time played. The heartbeat calls are sent every ten seconds. Heartbeats result in granular video engagement metrics and more accurate video fallout reports. streaming media services measure heartbeats using Adobe Launch with the Media Analytics extension, the Media SDK and the Media Collection API. The `AppMeasurement` and `VisitorID` components are used to receive video data.

Using heartbeats in streaming media services provides the following benefits:

| Feature | Description |
|---|---|
| Media Events | Detailed and Custom Events are sent every 10 seconds for main content and every 1 second for ads |
| Metrics and Dimensions | Clear standardized metrics, dimensions, and benchmarks across vendors. With a standardized solution across all platforms, you can use consistent, standardized variables across all of your media and platforms to allow for a more efficient cross-campaign, device and vendor comparison. |
| Integrations | Experience Cloud ID is linked to Adobe Experience Cloud for easier cross-analysis. With automatic Adobe Experience Cloud integration, you can segment your media audiences, target them, and make media recommendations based on user preferences. |
| Pricing | Transparent tracking by media stream (single) |
| Implementation and Support | Streamlined configuration with ongoing updates and improvements. With a streamlined implementation process, you can quickly map variables through your player API and validate implementations using the Adobe Debug Tool to ensure all necessary variables are tracked accurately. |
| Partner Sharing | Federated Media and Certified Metrics. With shared data through Federated Media, you can capitalize on our industry-first media sharing capabilities, to evaluate data holistically across all of your media distribution partners—operators, programmers, and distributors. |
| Advanced Tracking | Downloaded Content Tracking, Error Recovery Tracking and Concurrent Viewers. You can track streaming media content that is downloaded and played on a device regardless of its connectivity. |
