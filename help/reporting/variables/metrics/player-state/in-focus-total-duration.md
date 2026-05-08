---
title: In focus total duration
description: In focus total duration reports the cumulative seconds the player was in focus during a session.
feature: Metrics
role: User, Admin
---

# In focus total duration

>[!BEGINSHADEBOX]

*This page covers the **In focus total duration** reporting metric. See [In focus](/help/implementation/variables/player-state/in-focus.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **In focus total duration** metric reports the cumulative time, in seconds, that the player was in focus during a session. The backend sums every interval between a focus state-start and the matching state-end event.

## How this metric is calculated

The media backend sums elapsed time across all in-focus intervals during the session. The metric is reported on the close call. Analysis Workspace shows the value as `HH:MM:SS`; Data Feeds, Data Warehouse, and Reporting APIs show the value in seconds.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.infocus.time` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "inFocus"`, field `time` |
| Data feeds | `videostateinfocustime` |
