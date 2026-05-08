---
title: Ad name (dimension)
description: The Ad name dimension reports the human-readable title of each ad.
feature: Dimensions
role: User, Admin
---

# Ad name (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Ad name (dimension)**. See [Ad name (classification)](ad-name-class.md) for the corresponding Adobe Analytics classification derived from the same source value. See [Ad name](/help/implementation/variables/ads/ad-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad name** dimension reports the human-readable title of each ad. In Adobe Analytics this is the **Ad Name (dimension)**; the read-only [Ad name (classification)](ad-name-class.md) is automatically derived from the same value and joined to the Ad dimension.

## How this dimension is populated

Ad name is set by the player on every `media.adStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.friendlyName` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadname` |

## Dimension items

Each item is the literal ad title reported on `media.adStart` (for example, `"Ford F-150"`).
