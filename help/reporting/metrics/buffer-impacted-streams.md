---
title: Buffer impacted streams
description: Buffer impacted streams counts sessions in which the player entered a buffer state at least once.
feature: Metrics
role: User, Admin
---

# Buffer impacted streams

The **Buffer impacted streams** metric counts sessions in which the player entered a buffer state at least once. The metric is a session-level boolean — multiple buffer events within the same session count as one impacted stream. For total buffer volume, use [Buffer events](buffer-events.md).

## How this metric is calculated

The media backend sets `mediaReporting.qoeDataDetails.hasBufferImpactedStreams = true` the first time a `media.bufferStart` event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.buffer` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.hasBufferImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
