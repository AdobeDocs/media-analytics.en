---
title: Media time spent
description: Media time spent reports the total seconds of active playback per session, including ads.
feature: Metrics
role: User, Admin
---

# Media time spent

The **Media time spent** metric reports the total seconds of active playback per session, including both main content and ads but excluding pauses, buffering, and stalls. Use it to measure total time the viewer was actively engaged with the player. For main content only, use [Content time spent](content-time-spent.md).

## How this metric is calculated

The media backend sums the elapsed wall-clock time between events while the player is in the `play` state, on either main content or ads. Time during pauses, buffer events, and stalls is excluded. The metric is reported on the close call. The value is shown as `HH:MM:SS` in Analysis Workspace and in seconds in Data Feeds, Data Warehouse, and Reporting APIs.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.totalTimePlayed` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.totalTimePlayed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videototaltime` |
