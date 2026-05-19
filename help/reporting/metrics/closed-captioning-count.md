---
title: Closed captioning counts
description: Reports the number of times the viewer enabled captions during a session.
feature: Metrics
role: User, Admin
---

# Closed captioning counts

>[!BEGINSHADEBOX]

*This page covers the **Closed captioning counts** reporting metric. See [Closed captioning](/help/implementation/variables/player-state/closed-captioning.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Closed captioning counts** metric reports the number of times the viewer enabled captions during a session. Each caption-enable state-start event increments the count. Pair with [Streams impacted by closed captioning](closed-captioning-streams-impacted.md) for session-level boolean rollups and with [Closed captioning total duration](closed-captioning-total-duration.md) for total time in state.

## How this metric is calculated

The media backend increments this count on every caption-enable state-start event. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.closedcaptioning.count` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "closedCaptioning"`, field `count` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.closedcaptioning.count` |
