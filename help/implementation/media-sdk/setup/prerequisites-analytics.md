---
title: Prerequisites for Adobe Analytics-only implementations
description: Learn About Prerequisites for using the Adobe Analytics for Streaming Media Add-on for Adobe Analytics-only implementations
feature: Streaming Media, Workspace Basics
role: User, Admin, Data Engineer
exl-id: f94a5339-f777-44ec-ba79-0a1986c52225
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
