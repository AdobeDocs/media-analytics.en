---
title: Streams impacted by closed captioning
description: Counts sessions in which the viewer enabled captions at least once.
feature: Metrics
role: User, Admin
---

# Streams impacted by closed captioning

>[!BEGINSHADEBOX]

*This page covers the **Streams impacted by closed captioning** reporting metric. See [Closed captioning](/help/implementation/variables/player-state/closed-captioning.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Streams impacted by closed captioning** metric counts sessions in which the viewer enabled captions at least once. The metric is a session-level boolean — multiple caption toggles within the same session count as one impacted stream. For total caption-enable volume, use [Closed captioning counts](closed-captioning-count.md).

## How this metric is calculated

The media backend sets this flag the first time a caption-enable state-start event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.states.closedcaptioning.set` when [[!UICONTROL Player State Tracking]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.states[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details) entry where `name = "closedCaptioning"`, field `isSet` |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.states.closedcaptioning.set` |
