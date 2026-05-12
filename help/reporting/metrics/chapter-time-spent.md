---
title: Chapter time spent
description: Reports the total seconds of active playback per chapter.
feature: Metrics
role: User, Admin
---

# Chapter time spent

The **Chapter time spent** metric reports the total seconds of active playback per chapter. Pair it with [Chapter length](/help/reporting/dimensions/chapter-length.md) to compute the share of each chapter consumed.

## How this metric is calculated

The media backend sums the elapsed wall-clock time between events while the player is in the `play` state on a chapter. Time during pauses, buffering, and stalls is excluded. The metric is reported on the chapter close call. The value is shown as `HH:MM:SS` in Analysis Workspace and in seconds in Data Feeds, Data Warehouse, and Reporting APIs.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.chapter.timePlayed` when [[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.timePlayed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
