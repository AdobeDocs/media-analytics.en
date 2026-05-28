---
title: Chapter starts
description: Counts every chapter that began playing during a session.
feature: Metrics
role: User, Admin
---

# Chapter starts

The **Chapter starts** metric counts every chapter that began playing during a session. Pair it with [Chapter completes](chapter-completes.md) to compute the chapter completion rate.

## How this metric is calculated

The media backend sets this flag when a [chapter start](/help/implementation/events/chapters/chapter-start.md) event is received. The metric is reported on the chapter close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.chapter.view` when [[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.chapterDetails.isStarted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.chapter.view` |
