---
title: Buffer events (metric)
description: The Buffer events metric counts buffering events for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Buffer events (metric)

>[!BEGINSHADEBOX]

*This page covers the **Buffer events** metric. Adobe Analytics auto-populates a paired [Buffer events (dimension)](/help/reporting/variables/dimensions/quality/buffer-events.md) from the same `a.media.qoe.bufferCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.bufferCount` field that you can use as either a dimension or a metric.*

>[!ENDSHADEBOX]

The **Buffer events** metric counts buffering events across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute total buffer volume across a report period and to compare buffer-stability across content, networks, or players.

## How this metric is calculated

The media backend increments the count every time the player enters a `buffer` state. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bufferCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bufferCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |

For session-level boolean reporting (whether the session experienced any buffering at all), use [Buffer impacted streams](buffer-impacted-streams.md).
