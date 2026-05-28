---
title: Total pause duration
description: Reports the cumulative seconds the viewer spent paused during a session.
feature: Metrics
role: User, Admin
---

# Total pause duration

The **Total pause duration** metric reports the cumulative seconds the viewer spent paused during a session. The metric is the sum of all intervals between each [pause start](/help/implementation/events/playback/pause-start.md) event and the subsequent [play](/help/implementation/events/playback/play.md) event. Multiple pauses are added together. Pair with [Pause events](pause-events.md) to derive the average pause length.

## How this metric is calculated

The media backend sums the elapsed wall-clock time between every [pause start](/help/implementation/events/playback/pause-start.md) event and the matching [play](/help/implementation/events/playback/play.md) event. The metric is reported on the close call. The value is shown as `HH:MM:SS` in Analysis Workspace and in seconds elsewhere.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.pauseTime` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.pauseTime`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | N/A |
