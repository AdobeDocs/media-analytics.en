---
title: Drops before start
description: Drops before start counts sessions where the viewer quit before any main content rendered.
feature: Metrics
role: User, Admin
---

# Drops before start

The **Drops before start** metric counts sessions where the viewer quit before any main content rendered. The metric flags pre-content abandonment regardless of ad behavior, so it is the best measure of pure pre-content drop-off. Pair it with [Media starts](/help/reporting/variables/metrics/media-starts.md) and [Content starts](/help/reporting/variables/metrics/content-starts.md) to compute the share of sessions that never produced a content frame.

## How this metric is calculated

The media backend sets `mediaReporting.qoeDataDetails.isDroppedBeforeStart = true` for sessions that close without ever producing a `media.play` event on main content. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.dropBeforeStart` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.isDroppedBeforeStart`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
