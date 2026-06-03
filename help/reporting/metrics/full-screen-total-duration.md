---
title: Full screen total duration
description: Reports the cumulative seconds the viewer spent in full-screen during a session.
feature: Metrics
role: User, Admin
---

# Full screen total duration

>[!BEGINSHADEBOX]

*This page covers the **Full screen total duration** reporting metric. See [Full screen](/help/implementation/variables/player-state/full-screen.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Full screen total duration** metric reports the cumulative time, in seconds, that the viewer spent in full-screen during a session. The backend sums every interval between a full-screen state-start and the matching state-end event.

## How this metric is calculated

The media backend sums elapsed time across all full-screen intervals during the session. The metric is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.fullscreen.time` when [[!UICONTROL Player State Tracking]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "fullscreen"`, field `time` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.fullscreen.time` |
