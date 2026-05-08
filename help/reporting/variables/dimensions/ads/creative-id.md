---
title: Creative ID
description: The Creative ID dimension reports the ad creative identifier as a classification of the Ad dimension.
feature: Dimensions
role: User, Admin
---

# Creative ID

>[!BEGINSHADEBOX]

*This page covers the **Creative ID** reporting dimension. See [Creative ID](/help/implementation/variables/ads/creative-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Creative ID** dimension reports the ad creative identifier. In Adobe Analytics it is a classification of the Ad dimension that Adobe auto-populates from the value the player sets on `media.adStart`. In Customer Journey Analytics it is a discrete dimension. Use the dimension to roll up engagement across ads that share a creative.

## How this dimension is populated

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Ad dimension — Adobe automatically populates the classification from the latest `a.media.ad.creative` value reported for each ad. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.creativeID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `adclassificationcreative` |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a unique creative ID. Use a stable identifier per creative so the same creative rolls up to a single line item across campaigns.
