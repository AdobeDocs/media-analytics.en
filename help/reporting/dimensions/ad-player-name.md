---
title: Ad player name
description: Reports which player rendered each ad.
feature: Dimensions
role: User, Admin
---

# Ad player name

>[!BEGINSHADEBOX]

*This page covers the **Ad player name** reporting dimension. See [Ad player name](/help/implementation/variables/ads/ad-player-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad player name** dimension reports which player rendered each ad (for example, `"Freewheel"`, `"Google IMA"`). The ad player can differ from the main content player when ads are stitched in by a server-side ad insertion service.

## How this dimension is populated

Ad player name is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.playerName` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.playerName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadplayername`, `post_videoadplayername` |
| Audience Manager | `c_contextdata.a.media.ad.playerName` |

## Dimension items

Each item is the literal ad player name reported on [ad start](/help/implementation/events/ads/ad-start.md).
