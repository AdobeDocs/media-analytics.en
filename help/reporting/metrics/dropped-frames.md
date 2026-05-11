---
title: Dropped frames (metric)
description: The Dropped frames metric reports cumulative dropped frames for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Dropped frames (metric)

>[!BEGINSHADEBOX]

*This page covers the **Dropped frames** metric. Adobe Analytics auto-populates a paired [Dropped frames (dimension)](/help/reporting/dimensions/dropped-frames.md) from the same `a.media.qoe.droppedFrameCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.droppedFrames` field that you can use as either a dimension or a metric. See [Dropped frames](/help/implementation/variables/quality/dropped-frames.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Dropped frames** metric reports cumulative dropped frames across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute total drop volume in a report period and to compare frame-rendering quality across content, networks, or players.

## How this metric is calculated

The player updates the QoE object's `droppedFrames` value as drops accumulate. The backend reports the latest value on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.droppedFrameCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.droppedFrames`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |

For session-level boolean reporting (whether any frames were dropped at all), use [Dropped frame impacted streams](dropped-frame-impacted-streams.md).
