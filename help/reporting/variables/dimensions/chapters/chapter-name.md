---
title: Chapter name
description: The Chapter name dimension surfaces the human-readable chapter title as a classification of the Chapter dimension.
feature: Dimensions
role: User, Admin
---

# Chapter name

>[!BEGINSHADEBOX]

*This page covers the **Chapter name** classification of the [Chapter](chapter.md) dimension. See [Chapter name](/help/implementation/variables/chapters/chapter-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Chapter name** dimension surfaces the human-readable title of each chapter (for example, `"Pilot Episode - Opening"`). In Adobe Analytics it is a classification of the [Chapter](chapter.md) dimension. In Customer Journey Analytics it is a discrete dimension.

## How this dimension is populated

Chapter name is set by the player on every `media.chapterStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Chapter dimension — Adobe automatically populates the classification from the latest `a.media.chapter.friendlyName` value reported for each chapter. |
| Customer Journey Analytics | [`mediaReporting.chapterDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal chapter title reported on `media.chapterStart`.
