---
title: Chapter name
description: Surfaces the human-readable chapter title.
feature: Dimensions
role: User, Admin
---

# Chapter name

>[!BEGINSHADEBOX]

*This page covers the **Chapter name** reporting dimension. See [Chapter name](/help/implementation/variables/chapters/chapter-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Chapter name** dimension surfaces the human-readable title of each chapter (for example, `"Pilot Episode - Opening"`).

## How this dimension is populated

Chapter name is set by the player on every [chapter start](/help/implementation/events/chapters/chapter-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.chapter.friendlyName` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Chapter](chapter.md) dimension. Adobe automatically creates this classification when **[[!UICONTROL Media Chapters]](/help/reporting/setup/analytics-reporting.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`xdm.mediaReporting.chapterDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.chapter.friendlyName` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |
| Audience Manager | `c_contextdata.a.media.chapter.friendlyName` |

## Classification approach

Adobe creates the Chapter name classification structure automatically when **[[!UICONTROL Media Chapters]](/help/reporting/setup/analytics-reporting.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each chapter ID and its friendly name. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Chapter name classification name. Renaming it can cause Adobe to recreate the original classification, resulting in a duplicate.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.chapter.friendlyName` to an eVar. This approach captures the friendly name as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the chapter name and the parent [Chapter](chapter.md) dimension. If your implementation sends inconsistent values for the same chapter ID across events, multiple names can appear under the same chapter. Updating a value only applies to data moving forward.

## Dimension items

Each item is the literal chapter title reported on [chapter start](/help/implementation/events/chapters/chapter-start.md).
