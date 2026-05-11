---
title: Originator
description: The Originator dimension reports the creator or production studio of the content.
feature: Dimensions
role: User, Admin
---

# Originator

>[!BEGINSHADEBOX]

*This page covers the **Originator** reporting dimension. See [Originator](/help/implementation/variables/standard-metadata/originator.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Originator** dimension reports the creator or production studio of the content (for example, `"Warner Brothers"` or `"Sony"`). Use it to compare engagement across content owners or rights holders.

## How this dimension is populated

Originator is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the [Content (ID)](content.md) dimension, created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.originator`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

In Adobe Analytics, this dimension is a classification of the [Content (ID)](content.md) dimension. Adobe creates the classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [Originator](/help/implementation/variables/standard-metadata/originator.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Content (ID)](content.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal originator value reported at session start. Use a stable, distinct name per studio so engagement does not collapse across unrelated entities.
