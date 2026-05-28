---
title: Total stalling duration
description: Reports cumulative stall time for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Total stalling duration

The **Total stalling duration** metric reports cumulative stall time across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute total time viewers spent waiting on stalled playback in a report period.

In Customer Journey Analytics, `xdm.mediaReporting.qoeDataDetails.stallTime` can be used as either a metric or a dimension without a separate dimension component.

## How this metric is calculated

The media backend sums the duration of each stall interval, detected when no playhead movement is recorded on main content for at least three consecutive events. The metric is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.qoe.stallTime` to a custom event. |
| Customer Journey Analytics | [`xdm.mediaReporting.qoeDataDetails.stallTime`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (the custom event that your processing rule maps `a.media.qoe.stallTime` to; see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.qoe.stallTime` |
