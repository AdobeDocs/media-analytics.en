---
title: Stall events
description: Counts stall events for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Stall events

The **Stall events** metric counts stall events across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute total stall volume in a report period and to compare stall stability across content, networks, or players.

In Customer Journey Analytics, `mediaReporting.qoeDataDetails.stallCount` can be used as either a metric or a dimension without a separate dimension component.

## How this metric is calculated

The media backend increments the count each time no playhead movement is recorded on main content for at least three consecutive events. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.qoe.stallCount` to a custom event. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.stallCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (the custom event that your processing rule maps `a.media.qoe.stallCount` to; see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.qoe.stallCount` |

For session-level boolean reporting (whether any stall occurred at all), use [Stall impacted streams](stall-impacted-streams.md).
