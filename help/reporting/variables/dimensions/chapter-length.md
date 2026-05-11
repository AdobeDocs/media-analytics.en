---
title: Chapter length
description: The Chapter length dimension reports the duration of each chapter as a classification of the Chapter dimension.
feature: Dimensions
role: User, Admin
---

# Chapter length

>[!BEGINSHADEBOX]

*This page covers the **Chapter length** reporting dimension. See [Chapter length](/help/implementation/variables/chapters/chapter-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Chapter length** dimension reports the duration of each chapter, in seconds.

## How this dimension is populated

Chapter length is set by the player on every `media.chapterStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the [Chapter](chapter.md) dimension, created when **[[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

In Adobe Analytics, this dimension is a classification of the [Chapter](chapter.md) dimension. Adobe creates the classification when **[[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [Chapter length](/help/implementation/variables/chapters/chapter-length.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Chapter](chapter.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Media Chapters]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the integer length value, in seconds, reported on `media.chapterStart`.
