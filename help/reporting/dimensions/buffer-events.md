---
title: Buffer events (dimension)
description: Reports the count of buffering events per session.
feature: Dimensions
role: User, Admin
---

# Buffer events (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Buffer events** dimension. Adobe Analytics auto-populates a paired [Buffer events (metric)](/help/reporting/metrics/buffer-events.md) from the same `a.media.qoe.bufferCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.bufferCount` field that you can use as either a dimension or a metric.*

>[!ENDSHADEBOX]

The **Buffer events** dimension reports the count of buffering events that occurred during a session. Use the dimension to break out engagement by exact buffer count.

## How this dimension is populated

The media backend increments the count every time the player enters a `buffer` state. The value is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bufferCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bufferCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoebuffercountevar, post_videoqoebuffercountevar` |

## Dimension items

Each item is the literal buffer-count value reported on the close call. For session-level boolean reporting (whether the session experienced any buffering at all), use [Buffer impacted streams](/help/reporting/metrics/buffer-impacted-streams.md).
