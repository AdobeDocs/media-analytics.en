---
title: Media starts
description: Counts every media session that began, including sessions that ended in pre-roll ads or buffering.
feature: Metrics
role: User, Admin
---

# Media starts

The **Media starts** metric counts every media session that began. It is incremented as soon as the backend receives a [session start](/help/implementation/events/session/session-start.md) event, even if the viewer drops out during pre-roll ads, buffering, or before any main content plays. Use it as the broadest top-of-funnel metric for media reporting; pair it with [Content starts](content-starts.md) to measure ad and buffer drop-off.

## How this metric is calculated

The media backend sets this flag when a [session start](/help/implementation/events/session/session-start.md) event is received. The reported metric is `1` per session. Media starts is reported on the start call, not the close call; it is the only metric that does not wait for session close. All other media metrics, including [Content starts](/help/reporting/metrics/content-starts.md), [Content time spent](/help/reporting/metrics/content-time-spent.md), and [Progress markers](/help/reporting/metrics/progress-markers.md), are reported on the close call and are not available in real time during playback. [Ad starts](/help/reporting/metrics/ad-starts.md) is the one additional metric reported on its triggering event rather than at close.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.view` when [[!UICONTROL Media Core]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.isViewed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.view` |
