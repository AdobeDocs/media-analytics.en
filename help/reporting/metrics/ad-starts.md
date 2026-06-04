---
title: Ad starts
description: Counts every ad that began playing during a session.
feature: Metrics
role: User, Admin
---

# Ad starts

The **Ad starts** metric counts every ad that began playing during a session. Pair it with [Ad completes](ad-completes.md) to compute the ad completion rate, and with [Ad count](/help/reporting/metrics/ad-count.md) for the equivalent session-level rollup.

## How this metric is calculated

The media backend sets this flag when an [ad start](/help/implementation/events/ads/ad-start.md) event is received. The metric is reported on the ad start call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.view` when [[!UICONTROL Media Ads]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.isStarted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.ad.view` |
