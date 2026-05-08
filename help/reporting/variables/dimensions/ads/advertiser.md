---
title: Advertiser
description: The Advertiser dimension reports the company or brand featured in each ad.
feature: Dimensions
role: User, Admin
---

# Advertiser

>[!BEGINSHADEBOX]

*This page covers the **Advertiser** reporting dimension. See [Advertiser](/help/implementation/variables/ads/advertiser.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Advertiser** dimension reports the company or brand featured in each ad (for example, `"Ford"` or `"Coca-Cola"`). Use the dimension to break out engagement and completion by advertiser.

## How this dimension is populated

Advertiser is set by the player on every `media.adStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.advertiser` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.advertiser`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadadvertiser` |

## Dimension items

Each item is the literal advertiser name reported on `media.adStart`.
