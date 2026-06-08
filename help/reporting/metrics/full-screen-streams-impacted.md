---
title: Streams impacted by full screen
description: Counts sessions in which the viewer entered full-screen at least once.
feature: Metrics
role: User, Admin
---

# Streams impacted by full screen

>[!BEGINSHADEBOX]

*This page covers the **Streams impacted by full screen** reporting metric. See [Full screen](/help/implementation/variables/player-state/full-screen.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Streams impacted by full screen** metric counts sessions in which the viewer entered full-screen at least once. The metric is a session-level boolean; multiple full-screen entries within the same session count as one impacted stream. For total full-screen entry volume, use [Full screen counts](full-screen-count.md).

## How this metric is calculated

The media backend sets this flag the first time a full-screen state-start event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.fullscreen.set` when [[!UICONTROL Player State Tracking]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "fullscreen"`, field `isSet` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.fullscreen.set` |
