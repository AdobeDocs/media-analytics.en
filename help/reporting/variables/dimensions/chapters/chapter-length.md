---
title: Chapter length
description: The Chapter length dimension reports the duration of each chapter as a classification of the Chapter dimension.
feature: Dimensions
role: User, Admin
---

# Chapter length

>[!BEGINSHADEBOX]

*This page covers the **Chapter length** classification of the [Chapter](chapter.md) dimension. See [Chapter length](/help/implementation/variables/chapters/chapter-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Chapter length** dimension reports the duration of each chapter, in seconds. In Adobe Analytics it is a classification of the [Chapter](chapter.md) dimension. In Customer Journey Analytics it is a discrete dimension.

## How this dimension is populated

Chapter length is set by the player on every `media.chapterStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Chapter dimension — Adobe automatically populates the classification from the latest `a.media.chapter.length` value reported for each chapter. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the integer length value, in seconds, reported on `media.chapterStart`.
