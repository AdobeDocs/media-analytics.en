---
title: Paused impacted streams
description: Counts sessions in which the viewer paused at least once.
feature: Metrics
role: User, Admin
---

# Paused impacted streams

The **Paused impacted streams** metric counts sessions in which the viewer paused at least once. It is a session-level boolean. Multiple pauses within the same session count as one impacted stream. Use it to measure the share of sessions that experienced any pause; for total pause volume, use [Pause events](pause-events.md).

## How this metric is calculated

The media backend sets `mediaReporting.sessionDetails.hasPauseImpactedStreams = true` the first time a `media.pauseStart` event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.pause` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasPauseImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
