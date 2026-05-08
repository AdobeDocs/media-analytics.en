---
title: Bitrate changes (metric)
description: The Bitrate changes metric counts bitrate-change events for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Bitrate changes (metric)

>[!BEGINSHADEBOX]

*This page covers the **Bitrate changes** metric. Adobe Analytics auto-populates a paired [Bitrate changes (dimension)](/help/reporting/variables/dimensions/quality/bitrate-changes.md) from the same `a.media.qoe.bitrateChangeCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.bitrateChangeCount` field that you can use as either a dimension or a metric. See [Bitrate change](/help/implementation/variables/quality/bitrate-change.md) for how to fire bitrate-change events.*

>[!ENDSHADEBOX]

The **Bitrate changes** metric counts bitrate-change events across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute the total volume of bitrate changes in a report period and to compare bitrate-stability across content, networks, or players.

## How this metric is calculated

The media backend increments the count on every `media.bitrateChange` event received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bitrateChangeCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bitrateChangeCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoebitratechangecountevar` |

For session-level boolean reporting (whether the session experienced any bitrate change at all), use [Bitrate change impacted streams](bitrate-change-impacted-streams.md).
