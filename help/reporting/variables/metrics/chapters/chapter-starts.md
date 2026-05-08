---
title: Chapter starts
description: Chapter starts counts every chapter that began playing during a session.
feature: Metrics
role: User, Admin
---

# Chapter starts

The **Chapter starts** metric counts every chapter that began playing during a session. Pair it with [Chapter completes](chapter-completes.md) to compute the chapter completion rate.

## How this metric is calculated

The media backend sets `mediaReporting.chapterDetails.isStarted = true` when a `media.chapterStart` event is received. The metric is reported on the chapter close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.chapter.view` when [[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.isStarted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | `videochapterstart` |
