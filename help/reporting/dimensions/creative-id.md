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

The **Creative ID** dimension reports the ad creative identifier. Use the dimension to roll up engagement across ads that share a creative.

## How this dimension is populated

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the [Ad](ad.md) dimension, created when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.creativeID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `adclassificationcreative, post_adclassificationcreative` |

In Adobe Analytics, this dimension is a classification of the [Ad](ad.md) dimension. Adobe creates the classification when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [Creative ID](/help/implementation/variables/ads/creative-id.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Ad](ad.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a unique creative ID. Use a stable identifier per creative so the same creative rolls up to a single line item across campaigns.
