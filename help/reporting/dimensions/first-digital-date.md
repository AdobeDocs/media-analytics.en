---
title: First digital date
description: Reports the date the content first appeared on a digital platform.
feature: Dimensions
role: User, Admin
---

# First digital date

>[!BEGINSHADEBOX]

*This page covers the **First digital date** reporting dimension. See [First digital date](/help/implementation/variables/standard-metadata/first-digital-date.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **First digital date** dimension reports the date the content first appeared on a digital platform. Use it alongside [First air date](first-air-date.md) to compare digital release timing with original broadcast.

## How this dimension is populated

First digital date is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.digitalDate` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Content (ID)](content.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.firstDigitalDate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.digitalDate` to) |
| Data feeds (classification) | N/A — Data feeds do not include classification values. |

## Classification approach

Adobe creates the First digital date classification structure automatically when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification values using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each content ID and its first digital date. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the First digital date classification name. The classification is automatically created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.digitalDate` to an eVar. This method captures the first digital date as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the first digital date and the parent [Content (ID)](content.md) dimension. If your implementation sends inconsistent values for the same content ID across events, multiple first digital dates can appear under the same content.

## Dimension items

Each item is the literal date string reported at session start. Use a consistent format across implementations. Adobe recommends `YYYY-MM-DD`.
