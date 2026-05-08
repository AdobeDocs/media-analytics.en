---
title: Ad length (dimension)
description: The Ad length dimension reports the duration in seconds of each ad.
feature: Dimensions
role: User, Admin
---

# Ad length (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Ad length (dimension)**. See [Ad length (classification)](ad-length-class.md) for the corresponding Adobe Analytics classification derived from the same source value. See [Ad length](/help/implementation/variables/ads/ad-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad length** dimension reports the duration in seconds of each ad. In Adobe Analytics this is the **Ad Length (dimension)**; the read-only [Ad length (classification)](ad-length-class.md) is automatically derived from the same value and joined to the Ad dimension.

## How this dimension is populated

Ad length is set by the player on every `media.adStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.length` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadlength` |

## Dimension items

Each item is the literal ad length value, in seconds, reported on `media.adStart`. Group adjacent values into ranges using the Ad length classification.
