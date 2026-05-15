---
title: Campaign ID
description: Reports the campaign each ad belongs to.
feature: Dimensions
role: User, Admin
---

# Campaign ID

>[!BEGINSHADEBOX]

*This page covers the **Campaign ID** reporting dimension. See [Campaign ID](/help/implementation/variables/ads/campaign-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Campaign ID** dimension reports the ad campaign that each ad creative belongs to. Use the dimension to roll up engagement across multiple creatives that share a campaign.

## How this dimension is populated

Campaign ID is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.campaign` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.campaignID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videocampaign`, `post_videocampaign` |
| Audience Manager | `c_contextdata.a.media.ad.campaign` |

## Dimension items

Each item is the literal campaign value reported on [ad start](/help/implementation/events/ads/ad-start.md).
