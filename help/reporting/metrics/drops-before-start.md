---
title: Drops before start
description: Counts sessions where the viewer quit before any main content rendered.
feature: Metrics
role: User, Admin
---

# Drops before start

The **Drops before start** metric counts sessions where the viewer quit before any main content rendered. The metric flags pre-content abandonment regardless of ad behavior, so it is the best measure of pure pre-content drop-off. Pair it with [Media starts](/help/reporting/metrics/media-starts.md) and [Content starts](/help/reporting/metrics/content-starts.md) to compute the share of sessions that never produced a content frame.

## How this metric is calculated

The media backend sets this flag for sessions that close without ever producing a [play](/help/implementation/events/playback/play.md) event on main content. The metric is reported on the close call. Common scenarios include: the viewer exits during a pre-roll ad, the player stalls indefinitely in the initial buffer phase, or an error fires before the first main-content play event. In all these cases the session records a [Media start](/help/reporting/metrics/media-starts.md) but no [Content start](/help/reporting/metrics/content-starts.md), and no [Progress markers](/help/reporting/metrics/progress-markers.md) are recorded.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.dropBeforeStart` when [[!UICONTROL Media Quality]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.qoeDataDetails.isDroppedBeforeStart`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.qoe.dropBeforeStart` |
