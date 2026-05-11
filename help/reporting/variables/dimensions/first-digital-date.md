---
title: First digital date
description: The First digital date dimension reports the date the content first appeared on a digital platform.
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
| Adobe Analytics | Classification of the [Content (ID)](content.md) dimension, created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.firstDigitalDate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

In Adobe Analytics, this dimension is a classification of the [Content (ID)](content.md) dimension. Adobe creates the classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [First digital date](/help/implementation/variables/standard-metadata/first-digital-date.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Content (ID)](content.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal date string reported at session start. Use a consistent format across implementations. Adobe recommends `YYYY-MM-DD`.
