---
title: Ad time spent
description: Reports the total seconds of active ad playback per session.
feature: Metrics
role: User, Admin
---

# Ad time spent

The **Ad time spent** metric reports the total seconds of active ad playback per session, excluding pauses, buffering, and stalls. Pair it with [Content time spent](/help/reporting/metrics/content-time-spent.md) to compare ad load against content engagement.

## How this metric is calculated

The media backend sums the elapsed wall-clock time between events while the player is in the `play` state on an ad. Time during pauses, buffering, and seeks is excluded, consistent with how [Content time spent](/help/reporting/metrics/content-time-spent.md) is calculated for main content. The metric is reported on the ad close call. The value is shown as `HH:MM:SS` in Analysis Workspace and in seconds in Data Feeds, Data Warehouse, and Reporting APIs.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.timePlayed` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.timePlayed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.ad.timePlayed` |
