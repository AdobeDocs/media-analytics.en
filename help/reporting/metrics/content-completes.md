---
title: Content completes
description: Counts sessions whose playhead reached the end of the content.
feature: Metrics
role: User, Admin
---

# Content completes

The **Content completes** metric counts sessions whose playhead reached the end of the content. Pair it with [Content starts](content-starts.md) to compute the completion rate; pair with [Media starts](media-starts.md) to compute the end-to-end view rate.

## How this metric is calculated

The media backend sets this flag when a [session complete](/help/implementation/events/session/session-complete.md) event is received. The metric is reported on the close call. A session that times out without an explicit `sessionComplete` does not count as a completion.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.complete` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.isCompleted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.complete` |
