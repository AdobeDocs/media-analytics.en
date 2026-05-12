---
title: Time to start (metric)
description: Reports startup time for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Time to start (metric)

>[!BEGINSHADEBOX]

*This page covers the **Time to start** metric. Adobe Analytics auto-populates a paired [Time to start (dimension)](/help/reporting/dimensions/time-to-start.md) from the same `a.media.qoe.timeToStart` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.timeToStart` field that you can use as either a dimension or a metric. See [Time to start](/help/implementation/variables/quality/time-to-start.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Time to start** metric reports startup time across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute average startup time across a report period and to compare startup performance across content, networks, or players. Adobe stores the value in seconds and converts at ingest from the milliseconds the player reports.

## How this metric is calculated

The player sets `timeToStart` on the QoE object before session start fires. The backend reports the value on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.timeToStart` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.timeToStart`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
