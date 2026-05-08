---
title: Chapter offset
description: The Chapter offset dimension reports the offset of each chapter inside the content as a classification of the Chapter dimension.
feature: Dimensions
role: User, Admin
---

# Chapter offset

>[!BEGINSHADEBOX]

*This page covers the **Chapter offset** classification of the [Chapter](chapter.md) dimension. See [Chapter offset](/help/implementation/variables/chapters/chapter-offset.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Chapter offset** dimension reports the offset of each chapter inside the content, measured in seconds from the start. In Adobe Analytics it is a classification of the [Chapter](chapter.md) dimension. In Customer Journey Analytics it is a discrete dimension.

## How this dimension is populated

Chapter offset is set by the player on every `media.chapterStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Chapter dimension — Adobe automatically populates the classification from the latest `a.media.chapter.offset` value reported for each chapter. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.offset`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the integer offset value, in seconds, reported on `media.chapterStart`.
