---
title: Chapter position
description: Reports the index of each chapter inside the content.
feature: Dimensions
role: User, Admin
---

# Chapter position

>[!BEGINSHADEBOX]

*This page covers the **Chapter position** reporting dimension. See [Chapter position](/help/implementation/variables/chapters/chapter-position.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Chapter position** dimension reports the index of each chapter inside the content.

## How this dimension is populated

Chapter position is set by the player on every `media.chapterStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.chapter.position` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Chapter](chapter.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.index`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.chapter.position` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |

## Classification approach

Adobe creates the Chapter position classification structure automatically when **[[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification values using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each chapter ID and its position. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Chapter position classification name. The classification is automatically created when **[[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.chapter.position` to an eVar. This method captures the chapter position as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the chapter position and the parent [Chapter](chapter.md) dimension. If your implementation sends inconsistent values for the same chapter ID across events, multiple positions can appear under the same chapter.

## Dimension items

Each item is the integer position value reported on `media.chapterStart`.
