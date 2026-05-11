---
title: Ad completes
description: Ad completes counts every ad that played to completion.
feature: Metrics
role: User, Admin
---

# Ad completes

The **Ad completes** metric counts every ad that played to completion. Pair it with [Ad starts](ad-starts.md) to compute the ad completion rate.

## How this metric is calculated

The media backend sets `mediaReporting.advertisingDetails.isCompleted = true` when a `media.adComplete` event is received. The metric is reported on the ad close call. Ads that are skipped or abandoned do not count as completions.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.complete` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.isCompleted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
