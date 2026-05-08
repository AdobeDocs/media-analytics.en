---
title: Total buffer duration (metric)
description: The Total buffer duration metric reports cumulative buffer time for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Total buffer duration (metric)

>[!BEGINSHADEBOX]

*This page covers the **Total buffer duration** metric. Adobe Analytics auto-populates a paired [Total buffer duration (dimension)](/help/reporting/variables/dimensions/quality/total-buffer-duration.md) from the same `a.media.qoe.bufferTime` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.bufferTime` field that you can use as either a dimension or a metric.*

>[!ENDSHADEBOX]

The **Total buffer duration** metric reports cumulative buffer time across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute total time customers spent waiting on buffers in a report period.

## How this metric is calculated

The media backend sums the duration of every buffer interval (from `media.bufferStart` to the next state change). The metric is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bufferTime` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bufferTime`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoebuffertimeevar` |
