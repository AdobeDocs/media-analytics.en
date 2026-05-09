---
title: Picture in picture counts
description: Picture in picture counts reports the number of times the viewer entered picture-in-picture during a session.
feature: Metrics
role: User, Admin
---

# Picture in picture counts

>[!BEGINSHADEBOX]

*This page covers the **Picture in picture counts** reporting metric. See [Picture in picture](/help/implementation/variables/player-state/picture-in-picture.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Picture in picture counts** metric reports the number of times the viewer entered picture-in-picture playback during a session. Each picture-in-picture state-start event increments the count. Pair with [Streams impacted by picture in picture](picture-in-picture-streams-impacted.md) for session-level boolean rollups and with [Picture in picture total duration](picture-in-picture-total-duration.md) for total time in state.

## How this metric is calculated

The media backend increments the `count` field in the `pictureInPicture` entry of `mediaReporting.states[]` on every picture-in-picture state-start event. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.pictureinpicture.count` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "pictureInPicture"`, field `count` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
