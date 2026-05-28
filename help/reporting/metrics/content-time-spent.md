---
title: Content time spent
description: Reports the total seconds of active main-content playback per session.
feature: Metrics
role: User, Admin
---

# Content time spent

The **Content time spent** metric reports the total seconds of active main-content playback per session, excluding ads, pauses, buffering, and stalls. Use it as the engagement metric for content viewing; for time spent including ads, see [Media time spent](media-time-spent.md).

## How this metric is calculated

The media backend sums the elapsed wall-clock time between events while the player is in the `play` state on main content. Time during ads, pauses, buffer events, and stalls is excluded. Because only active play time is counted, the metric can exceed [Content length](/help/reporting/dimensions/content-length.md) when a viewer seeks backward and re-watches a segment. Each pass through a given segment accumulates additional play time, and can accrue for as long as the user consumes and rewinds content in a session. The metric is reported on the close call. The value is shown as `HH:MM:SS` in Analysis Workspace and in seconds in Data Feeds, Data Warehouse, and Reporting APIs.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.timePlayed` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.timePlayed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.timePlayed` |
