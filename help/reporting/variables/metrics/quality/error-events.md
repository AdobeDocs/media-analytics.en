---
title: Error events
description: The Error events metric counts error events for sums and averages across sessions.
feature: Metrics
role: User, Admin
---

# Error events

>[!BEGINSHADEBOX]

*This page covers the **Error events** metric. Adobe Analytics auto-populates a paired [Errors dimension](/help/reporting/variables/dimensions/quality/errors.md) from the same `a.media.qoe.errorCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.errorCount` field that you can use as either a dimension or a metric.*

>[!ENDSHADEBOX]

The **Error events** metric counts error events across sessions, suitable for sums, averages, and percentile rollups. Use the metric to compute total error volume in a report period and to compare error rates across content, networks, or players.

## How this metric is calculated

The media backend increments the count on every error reported by the player. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.errorCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.errorCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoeerrorcountevar` |

For session-level boolean reporting (whether any error occurred at all), use [Error impacted streams](error-impacted-streams.md).
