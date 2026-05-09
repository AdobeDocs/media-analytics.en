---
title: Total buffer duration (dimension)
description: The Total buffer duration dimension reports the cumulative seconds spent buffering per session.
feature: Dimensions
role: User, Admin
---

# Total buffer duration (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Total buffer duration** dimension. Adobe Analytics auto-populates a paired [Total buffer duration (metric)](/help/reporting/variables/metrics/quality/total-buffer-duration.md) from the same `a.media.qoe.bufferTime` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.bufferTime` field that you can use as either a dimension or a metric.*

>[!ENDSHADEBOX]

The **Total buffer duration** dimension reports the cumulative time, in seconds, that the player spent in a buffer state during a session. Use the dimension to break out engagement by exact buffer-duration value.

## How this dimension is populated

The media backend sums the duration of every buffer interval (from `media.bufferStart` to the next state change). The value is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bufferTime` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bufferTime`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoebuffertimeevar, post_videoqoebuffertimeevar` |

## Dimension items

Each item is the literal duration value, in seconds, reported on the close call.
