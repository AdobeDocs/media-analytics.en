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

The **Asset ID** dimension reports a stable industry identifier for the underlying media asset (typically an EIDR, TMS/Gracenote, or Rovi ID, but proprietary IDs are also accepted). In Adobe Analytics it is a classification of Content (ID); in Customer Journey Analytics it is a discrete dimension.

## How this dimension is populated

Asset ID is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Content (ID) dimension — Adobe automatically populates the classification from the latest `a.media.asset` value reported for each content ID. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.assetID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a unique asset ID value reported during the report period. Use a single stable identifier per asset across all distribution platforms so the same content rolls up to a single line item.
