---
title: Chapter count
description: Chapter count reports the number of chapters that started during a session.
feature: Metrics
role: User, Admin
---

# Chapter count

The **Chapter count** metric reports the number of chapters that started during a session. Use it to compare chapter consumption across content. For chapter start counts pivoted by chapter dimensions (chapter name, position), use the Chapter starts metric available when the Chapters variable category is enabled.

## How this metric is calculated

The media backend increments `mediaReporting.sessionDetails.chapterCount` on every `media.chapterStart` event received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.chapterCount` to a free event. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.chapterCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A |
