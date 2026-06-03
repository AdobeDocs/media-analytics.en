---
title: Closed captioning total duration
description: Reports the cumulative seconds captions were enabled during a session.
feature: Metrics
role: User, Admin
---

# Closed captioning total duration

>[!BEGINSHADEBOX]

*This page covers the **Closed captioning total duration** reporting metric. See [Closed captioning](/help/implementation/variables/player-state/closed-captioning.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Closed captioning total duration** metric reports the cumulative time, in seconds, that captions were enabled during a session. The backend sums every interval between a caption-enable state-start and the matching state-end event.

## How this metric is calculated

The media backend sums elapsed time across all caption-enabled intervals during the session. The metric is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.closedcaptioning.time` when [[!UICONTROL Player State Tracking]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "closedCaptioning"`, field `time` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.closedcaptioning.time` |
