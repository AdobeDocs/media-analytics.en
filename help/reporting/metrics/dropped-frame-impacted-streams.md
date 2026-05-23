---
title: Dropped frame impacted streams
description: Counts sessions in which at least one frame was dropped.
feature: Metrics
role: User, Admin
---

# Dropped frame impacted streams

The **Dropped frame impacted streams** metric counts sessions in which at least one frame was dropped. The metric is a session-level boolean — multiple drops within the same session count as one impacted stream. For total drop volume, use [Dropped frames](dropped-frames.md).

## How this metric is calculated

The media backend sets this flag if the QoE object's `droppedFrames` value is greater than zero at session close.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.droppedFrames` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.hasDroppedFrameImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.qoe.droppedFrames` |
