---
title: Media concurrent viewers
description: Learn about the Media Concurrent Viewers dashboard used to display concurrent viewers during one day. Data can be filtered by content, device type, or country.
uuid: e61c50e5-8196-4538-b67c-ebc01c6e6ba7
exl-id: 2c679c1a-a4bd-44fc-8e11-173c8544ab06
feature: Streaming Media, Workspace Basics
role: User, Admin
TQID: https://experienceleague.adobe.com/8pqoGpVCRXvovD-cNPNOvFQFvJco3sWUq3SuXEOVeJI
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: c153fd90-23e1-4614-81d3-3cc7571227f7
    internal-label: Analysis Workspace
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e38cbddc-1633-4cd5-bed5-9f289f2a6029
    internal-label: Panels
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
---
# Media concurrent viewers reports {#media-concurrent-viewers}

The Media Concurrent Viewers dashboard displays concurrent viewers during one day. The data can be filtered by content, device type, or country.

>[!TIP]
>
> This report is based on concurrent active media sessions.  To see concurrent viewers by unique visitor, with the additional capabilities to apply a segment, break down and compare, use the [Media Concurrent Viewers panel in Analysis Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/panels/media-concurrent-viewers.html).
>

![](assets/video-concurrent-viewers.png)

## Report features {#report-features}

Here are some features of this report:

* This is not in real time. It has normal Adobe Analytics latency.
* The report covers a 24 hour time frame. The x-axis is time-of-day based on the report suite time zone.
* This shows concurrent viewers at minute granularity.
* There is a *Media Concurrent Viewers Report* that shows how many viewers are watching or listening across all content.
* There is a Concurrent Viewers report within the *Media Detail* report that shows how many viewers are watching or listening to one specific media item.
* The report only works across one day.
* The customer can look at historical concurrent viewer reports (limited to a single day).

## Limitations {#limitations}

Here are some limitations for this report:

* No data will be displayed if the selected interval is not an entire day.
* You cannot export the data, such as ReportBuilder.
* You cannot present the data in a table format.
* You cannot send a report via email.
* Even if you do not track ads, you have to re-enable media tracking and select the Media Ad module.
* This functionality will provide accurate data when using a heartbeats Library that has Pause tracking capabilities.
