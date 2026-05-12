---
title: First air date
description: Reports the date the content first aired on television.
feature: Dimensions
role: User, Admin
---

# First air date

>[!BEGINSHADEBOX]

*This page covers the **First air date** reporting dimension. See [First air date](/help/implementation/variables/standard-metadata/first-air-date.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **First air date** dimension reports the date the content first aired on television. Use it to separate engagement on new releases from engagement on older content.

## How this dimension is populated

First air date is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.airDate` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Content (ID)](content.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.firstAirDate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.airDate` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |

## Classification approach

Adobe creates the First air date classification structure automatically when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each content ID and its first air date. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the First air date classification name. Renaming it can cause Adobe to recreate the original classification, resulting in a duplicate.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.airDate` to an eVar. This approach captures the first air date as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the first air date and the parent [Content (ID)](content.md) dimension. If your implementation sends inconsistent values for the same content ID across events, multiple first air dates can appear under the same content. Updating a value only applies to data moving forward.

## Dimension items

Each item is the literal date string reported at session start. Use a consistent format across implementations. Adobe recommends `YYYY-MM-DD`.
