---
title: Streams impacted by picture in picture
description: Streams impacted by picture in picture counts sessions in which the viewer entered picture-in-picture at least once.
feature: Metrics
role: User, Admin
---

# Streams impacted by picture in picture

>[!BEGINSHADEBOX]

*This page covers the **Streams impacted by picture in picture** reporting metric. See [Picture in picture](/help/implementation/variables/player-state/picture-in-picture.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Streams impacted by picture in picture** metric counts sessions in which the viewer entered picture-in-picture playback at least once. The metric is a session-level boolean — multiple picture-in-picture entries within the same session count as one impacted stream. For total picture-in-picture entry volume, use [Picture in picture counts](picture-in-picture-count.md).

## How this metric is calculated

The media backend sets the `isSet` flag in `mediaReporting.states[]` for the `pictureInPicture` entry to `true` the first time a `media.statesUpdate` event with `pictureInPicture` in `statesStart` is received. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.pictureinpicture.set` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "pictureInPicture"`, field `isSet` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
