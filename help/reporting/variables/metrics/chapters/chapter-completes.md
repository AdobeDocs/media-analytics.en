---
title: Chapter completes
description: Chapter completes counts every chapter that played to completion.
feature: Metrics
role: User, Admin
---

# Chapter completes

The **Chapter completes** metric counts every chapter that played to completion. Pair it with [Chapter starts](chapter-starts.md) to compute the chapter completion rate.

## How this metric is calculated

The media backend sets `mediaReporting.chapterDetails.isCompleted = true` when a `media.chapterComplete` event is received. The metric is reported on the chapter close call. Chapters skipped or abandoned mid-play do not count as completions.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.chapter.complete` when [[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.isCompleted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | `videochaptercomplete` |
