---
title: Dropped frames (dimension)
description: The Dropped frames dimension reports the cumulative dropped-frame count per session.
feature: Dimensions
role: User, Admin
---

# Dropped frames (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Dropped frames** dimension. Adobe Analytics auto-populates a paired [Dropped frames (metric)](/help/reporting/variables/metrics/dropped-frames.md) from the same `a.media.qoe.droppedFrameCount` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.droppedFrames` field that you can use as either a dimension or a metric. See [Dropped frames](/help/implementation/variables/quality/dropped-frames.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Dropped frames** dimension reports the cumulative count of frames dropped during a session. Use the dimension to break out engagement by exact drop count.

## How this dimension is populated

The player updates the QoE object's `droppedFrames` value as it accumulates drops. The backend reports the latest value on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.droppedFrameCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.droppedFrames`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoedroppedframecountevar, post_videoqoedroppedframecountevar` |

## Dimension items

Each item is the literal drop-count value reported on the close call. For session-level boolean reporting (whether any frames were dropped at all), use [Dropped frame impacted streams](/help/reporting/variables/metrics/dropped-frame-impacted-streams.md).
