---
title: Ad name
description: The Ad name dimension reports the human-readable title of each ad.
feature: Dimensions
role: User, Admin
---

# Ad name

>[!BEGINSHADEBOX]

*This page covers the **Ad name** reporting dimension. See [Ad name](/help/implementation/variables/ads/ad-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad name** dimension reports the human-readable title of each ad.

## How this dimension is populated

Ad name is set by the player on every `media.adStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.friendlyName` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadname, post_videoadname` |

>[!NOTE]
>
>In Adobe Analytics, this value appears two ways: as **Ad name (variable)** (collected directly from `a.media.ad.friendlyName`) and as **Ad name** (a classification derived from the [Ad](ad.md) dimension). Use whichever component that your implementation workflow best supports.

## Dimension items

Each item is the literal ad title reported on `media.adStart` (for example, `"Ford F-150"`).
