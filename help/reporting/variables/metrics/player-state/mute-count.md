---
title: Mute counts
description: Mute counts reports the number of times the viewer muted audio during a session.
feature: Metrics
role: User, Admin
---

# Mute counts

>[!BEGINSHADEBOX]

*This page covers the **Mute counts** reporting metric. See [Mute](/help/implementation/variables/player-state/mute.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Mute counts** metric reports the number of times the viewer muted audio during a session. Each mute state-start event increments the count. Pair with [Streams impacted by mute](mute-streams-impacted.md) for session-level boolean rollups and with [Mute total duration](mute-total-duration.md) for total time in state.

## How this metric is calculated

The media backend increments the `count` field in the `mute` entry of `mediaReporting.states[]` on every mute state-start event. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.mute.count` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "mute"`, field `count` |
| Data feeds | `videostatemutecount` |
