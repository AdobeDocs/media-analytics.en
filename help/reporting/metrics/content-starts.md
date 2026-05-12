---
title: Content starts
description: Counts sessions in which main content actually began playing.
feature: Metrics
role: User, Admin
---

# Content starts

The **Content starts** metric counts sessions in which main content actually began playing. Unlike [Media starts](media-starts.md), it excludes sessions that ended during pre-roll ads, buffering, or stalls. This makes it the right denominator for completion and engagement rates.

## How this metric is calculated

The media backend sets `mediaReporting.sessionDetails.isPlayed = true` the first time a `media.play` event for main content is received. The metric is triggered on that play event but reported on the close call. To compute the pre-roll drop rate, use `(Media starts − Content starts) / Media starts`.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.play` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.isPlayed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
