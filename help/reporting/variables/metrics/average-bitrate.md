---
title: Average bitrate (metric)
description: The Average bitrate metric reports the raw weighted-average bitrate of each session, in kbps.
feature: Metrics
role: User, Admin
---

# Average bitrate (metric)

>[!BEGINSHADEBOX]

*This page covers the **Average bitrate** event metric, which reports the raw weighted-average bitrate per session. See [Average bitrate (dimension)](/help/reporting/variables/dimensions/average-bitrate.md) for the bucketed dimension. See [Bitrate](/help/implementation/variables/quality/bitrate.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Average bitrate** metric reports the raw weighted-average playback bitrate, in kbps, for each session. Unlike the [bucketed dimension](/help/reporting/variables/dimensions/average-bitrate.md), the metric is a continuous numeric value suitable for sums, averages, and percentile rollups across sessions.

## How this metric is calculated

The media backend computes a weighted average of all bitrate values reported during the session, weighted by the duration each bitrate was active. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bitrateAverage` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.bitrateAverage`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
