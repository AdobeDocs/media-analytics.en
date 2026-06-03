---
title: Chapter
description: Reports each unique chapter played, keyed by an auto-generated chapter ID.
feature: Dimensions
role: User, Admin
---

# Chapter

The **Chapter** dimension reports each unique chapter played, keyed by an auto-generated chapter ID. The ID is constructed by the SDK or backend from the content ID, chapter index, and chapter start time, so two sessions of the same chapter on the same content roll up to a single line item. Use the dimension as the join key for chapter-level classifications such as Chapter name, Chapter length, Chapter offset, and Chapter position.

## How this dimension is populated

The Chapter ID is generated automatically when a [chapter start](/help/implementation/events/chapters/chapter-start.md) event fires. The value is not set directly; it is derived from chapter position, offset, and content ID.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.chapter.name` when [[!UICONTROL Media Chapters]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.chapterDetails.ID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/chapter-details-reporting) |
| Data feeds | `videochapter`, `post_videochapter` |
| Audience Manager | N/A |

## Dimension items

Each item is a unique chapter ID. The ID is opaque (typically a hash of content ID + index + offset) and is most useful as a grouping key. Pair with [Chapter name](chapter-name.md) for a friendly label.
