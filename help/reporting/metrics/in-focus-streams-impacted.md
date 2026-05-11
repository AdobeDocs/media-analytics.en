---
title: Streams impacted by in focus
description: Streams impacted by in focus counts sessions in which the player was in focus at least once.
feature: Metrics
role: User, Admin
---

# Streams impacted by in focus

>[!BEGINSHADEBOX]

*This page covers the **Streams impacted by in focus** reporting metric. See [In focus](/help/implementation/variables/player-state/in-focus.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Streams impacted by in focus** metric counts sessions in which the player was in focus at least once. The metric is a session-level boolean — multiple focus events within the same session count as one impacted stream. For total focus event volume, use [In focus counts](in-focus-count.md).

## How this metric is calculated

The media backend sets the `isSet` flag in `mediaReporting.states[]` for the `inFocus` entry to `true` the first time a `media.statesUpdate` event with `inFocus` in `statesStart` is received. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.infocus.set` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "inFocus"`, field `isSet` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
