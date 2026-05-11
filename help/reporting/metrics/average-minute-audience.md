---
title: Average minute audience
description: Average minute audience reports the average number of viewers watching at any given minute across the content's runtime.
feature: Metrics
role: User, Admin
---

# Average minute audience

The **Average minute audience** metric reports the average number of viewers watching at any given minute across the content's runtime. It is the standard "AMA" measure used to compare media reach across content of different lengths.

## How this metric is calculated

The media backend computes Average minute audience per session as `Content time spent / Content length`. When summed across sessions, the total represents the average audience size at each minute of the content. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.averageMinuteAudience` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.averageMinuteAudience`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |

>[!IMPORTANT]
>
>Average minute audience requires a non-zero [Content length](/help/reporting/dimensions/content-length.md). If content length is unset or zero, this metric is not produced for the session.
