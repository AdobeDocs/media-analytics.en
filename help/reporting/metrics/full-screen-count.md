---
title: Full screen counts
description: Reports the number of times the viewer entered full-screen during a session.
feature: Metrics
role: User, Admin
---

# Full screen counts

>[!BEGINSHADEBOX]

*This page covers the **Full screen counts** reporting metric. See [Full screen](/help/implementation/variables/player-state/full-screen.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Full screen counts** metric reports the number of times the viewer entered full-screen during a session. Each full-screen state-start event increments the count. Pair with [Streams impacted by full screen](full-screen-streams-impacted.md) for session-level boolean rollups and with [Full screen total duration](full-screen-total-duration.md) for total time in state.

## How this metric is calculated

This count is incremented on every full-screen state-start event. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.fullscreen.count` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "fullscreen"`, field `count` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.fullscreen.count` |
