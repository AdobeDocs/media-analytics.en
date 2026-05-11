---
title: Asset ID
description: The Asset ID dimension reports a stable industry identifier for the underlying media asset.
feature: Dimensions
role: User, Admin
---

# Asset ID

>[!BEGINSHADEBOX]

*This page covers the **Asset ID** reporting dimension. See [Asset ID](/help/implementation/variables/standard-metadata/asset-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Asset ID** dimension reports a stable industry identifier for the underlying media asset (typically an EIDR, TMS/Gracenote, or Rovi ID, but proprietary IDs are also accepted).

## How this dimension is populated

Asset ID is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the [Content (ID)](content.md) dimension, created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.assetID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

In Adobe Analytics, this dimension is a classification of the [Content (ID)](content.md) dimension. Adobe creates the classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [Asset ID](/help/implementation/variables/standard-metadata/asset-id.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Content (ID)](content.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a unique asset ID value reported during the report period. Use a single stable identifier per asset across all distribution platforms so the same content rolls up to a single line item.
