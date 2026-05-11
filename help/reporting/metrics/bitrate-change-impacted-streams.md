---
title: Bitrate change impacted streams
description: Bitrate change impacted streams counts sessions in which at least one bitrate change occurred.
feature: Metrics
role: User, Admin
---

# Bitrate change impacted streams

The **Bitrate change impacted streams** metric counts sessions in which at least one bitrate change occurred. The metric is a session-level boolean — multiple bitrate changes within the same session count as one impacted stream. For total bitrate-change volume, use [Bitrate changes](/help/reporting/dimensions/bitrate-changes.md).

## How this metric is calculated

The media backend sets `mediaReporting.qoeDataDetails.hasBitrateChangeImpactedStreams = true` the first time a `media.bitrateChange` event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bitrateChange` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.hasBitrateChangeImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
