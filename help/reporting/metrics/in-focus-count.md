---
title: In focus counts
description: Reports the number of times the player gained focus during a session.
feature: Metrics
role: User, Admin
---

# In focus counts

>[!BEGINSHADEBOX]

*This page covers the **In focus counts** reporting metric. See [In focus](/help/implementation/variables/player-state/in-focus.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **In focus counts** metric reports the number of times the player gained focus during a session. Each focus state-start event increments the count. Pair with [Streams impacted by in focus](in-focus-streams-impacted.md) for session-level boolean rollups and with [In focus total duration](in-focus-total-duration.md) for total time in state.

## How this metric is calculated

The media backend increments the `count` field in the `inFocus` entry of `mediaReporting.states[]` on every focus state-start event. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.infocus.count` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "inFocus"`, field `count` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.infocus.count` |
