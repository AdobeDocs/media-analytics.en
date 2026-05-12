---
title: Prerequisites for Adobe Analytics-only implementations
description: Learn About Prerequisites for using the Adobe Analytics for Streaming Media Add-on for Adobe Analytics-only implementations
feature: Streaming Media, Workspace Basics
role: User, Admin, Developer
exl-id: f94a5339-f777-44ec-ba79-0a1986c52225
TQID: https://experienceleague.adobe.com/falbDtUtqAMtmtQs2jLpEvUKmwvATotVu8njuTNZ09k
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
  - id: c77ba355-6681-41fe-b719-563d3f507fdb
    internal-label: Mobile SDK
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
# Prerequisites for Adobe Analytics-only implementations

The prerequisites described in this section are specific to implementing the Adobe Analytics for Streaming Media Add-on for Adobe-Analytics-only implementations (when not using Edge).

1. **Complete the general prerequisites**<br>
Whether you implement streaming media services for Adobe Analytics-only implementations or for Edge implementations, ensure that you meet the [general prerequisites](/help/getting-started/prereqs.md).

1. **Confirm that you have an Adobe Analytics implementation**<br>
When implementing the Adobe Analytics for Streaming Media Add-on for an Analytics-only implementation, an Adobe Analytics basic implementation is also required. See [Implement Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html) for more information.

1. **Obtain the media tracking server URL**<br>
Ask your Adobe Analytics Representative for the media tracking server URL. This is the `collection-api-server` URL for the Mobile SDK, the JavaScript SDK, and the non-collection-api tracking server for Roku. Domain names for API implementation is: `[your_namespace].hb-api.omtrdc.net`.

1. **Download the current Media SDK or implement the required Extensions**<br>
Depending on the implementation path, [download the current SDK](/help/getting-started/download-sdks.md) for web, mobile, or over-the-top platforms. The required extensions must be implemented to enable the Adobe Analytics for Streaming Media Add-on.

1. **Enable Adobe Analytics Reports**<br>
To enable reports in Analytics and to view the content and ad data that you're collecting, you must enable reports in Analytics. See [Media reports enablement](/help/reporting/media-reports-enable.md).
