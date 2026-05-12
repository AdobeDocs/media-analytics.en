---
title: Pause events
description: Counts every distinct pause that occurred during a session.
feature: Metrics
role: User, Admin
---

# Pause events

The **Pause events** metric counts every distinct `media.pauseStart` event received during a session, including multiple pauses within the same session. Pair it with [Total pause duration](total-pause-duration.md) to derive the average pause length, and with [Paused impacted streams](paused-impacted-streams.md) to count sessions that paused at least once.

## How this metric is calculated

The media backend increments `mediaReporting.sessionDetails.pauseCount` on every `media.pauseStart` event. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.pauseCount` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.pauseCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
