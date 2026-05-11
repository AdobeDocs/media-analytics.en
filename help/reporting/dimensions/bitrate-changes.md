---
title: Bitrate changes (dimension)
description: The Bitrate changes dimension reports the count of bitrate-change events per session.
feature: Dimensions
role: User, Admin
---

# Bitrate changes (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Bitrate changes** dimension. Adobe Analytics auto-populates a paired [Bitrate changes (metric)](/help/reporting/metrics/bitrate-changes.md) from the same `a.media.qoe.bitrateChangeCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.bitrateChangeCount` field that you can use as either a dimension or a metric. See [Bitrate change](/help/implementation/variables/quality/bitrate-change.md) for how to fire bitrate-change events.*

>[!ENDSHADEBOX]

The **Bitrate changes** dimension reports the count of bitrate-change events that occurred during a session. Use the dimension to break out engagement and quality by exact change-count value (for example, "sessions with 3 bitrate changes vs. sessions with 0").

## How this dimension is populated

The media backend increments the count on every `media.bitrateChange` event received during the session. The value is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bitrateChangeCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bitrateChangeCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoebitratechangecountevar, post_videoqoebitratechangecountevar` |

## Dimension items

Each item is the literal change-count value reported on the close call. For session-level boolean reporting (whether the session experienced any bitrate change at all), use [Bitrate change impacted streams](/help/reporting/metrics/bitrate-change-impacted-streams.md).
