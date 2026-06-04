---
title: Streams impacted by mute
description: Counts sessions in which the viewer muted audio at least once.
feature: Metrics
role: User, Admin
---

# Streams impacted by mute

>[!BEGINSHADEBOX]

*This page covers the **Streams impacted by mute** reporting metric. See [Mute](/help/implementation/variables/player-state/mute.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Streams impacted by mute** metric counts sessions in which the viewer muted audio at least once. The metric is a session-level boolean — multiple mute toggles within the same session count as one impacted stream. For total mute volume, use [Mute counts](mute-count.md).

## How this metric is calculated

The media backend sets this flag the first time a mute state-start event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.mute.set` when [[!UICONTROL Player State Tracking]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "mute"`, field `isSet` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.mute.set` |
