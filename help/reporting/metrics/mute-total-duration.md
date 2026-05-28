---
title: Mute total duration
description: Reports the cumulative seconds audio was muted during a session.
feature: Metrics
role: User, Admin
---

# Mute total duration

>[!BEGINSHADEBOX]

*This page covers the **Mute total duration** reporting metric. See [Mute](/help/implementation/variables/player-state/mute.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Mute total duration** metric reports the cumulative time, in seconds, that audio was muted during a session. The backend sums every interval between a mute state-start and the matching state-end event.

## How this metric is calculated

The media backend sums elapsed time across all mute intervals during the session. The metric is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.mute.time` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "mute"`, field `time` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.mute.time` |
