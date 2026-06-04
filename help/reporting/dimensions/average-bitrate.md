---
title: Average bitrate (dimension)
description: Reports the bucketed average bitrate of each session in 100-kbps intervals.
feature: Dimensions
role: User, Admin
---

# Average bitrate (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Average bitrate** dimension, which reports the bucketed bitrate of each session. See [Average bitrate (metric)](/help/reporting/metrics/average-bitrate.md) for the raw weighted-average metric. See [Bitrate](/help/implementation/variables/quality/bitrate.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Average bitrate** dimension reports the average playback bitrate per session, bucketed in 100-kbps intervals. The backend computes the value as a weighted average of all bitrate values across the session, then assigns it to a bucket. Use the dimension to break out engagement and quality by bitrate tier.

## How this dimension is populated

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.bitrateAverageBucket` when [[!UICONTROL Media Quality]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.qoeDataDetails.bitrateAverageBucket`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoebitrateaverageevar`, `post_videoqoebitrateaverageevar` |
| Audience Manager | `c_contextdata.a.media.qoe.bitrateAverageBucket` |

## Dimension items

Each item is a bitrate bucket label (for example, `800-899`, `3200-3299`). Use the [Average bitrate (metric)](/help/reporting/metrics/average-bitrate.md) for a raw weighted-average value rather than a bucketed dimension.
