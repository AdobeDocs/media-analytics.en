---
title: Ad length
description: Reports the duration in seconds of each ad.
feature: Dimensions
role: User, Admin
---

# Ad length

>[!BEGINSHADEBOX]

*This page covers the **Ad length** reporting dimension. See [Ad length](/help/implementation/variables/ads/ad-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad length** dimension reports the duration in seconds of each ad.

## How this dimension is populated

Ad length is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.length` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadlength`, `post_videoadlength` |
| Audience Manager | `c_contextdata.a.media.ad.length` |

In Adobe Analytics, this dimension appears two ways: as **Ad length (variable)** (collected directly from `a.media.ad.length`) and as **Ad length** (a classification derived from the [Ad](ad.md) dimension). If you use the classification, you are responsible for populating and maintaining its values using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). Using **Ad length (variable)** requires no classification maintenance, but you lose the guaranteed 1:1 relationship between the ad length and the parent [Ad](ad.md) dimension. Use whichever component your implementation workflow best supports.

## Dimension items

Each item is the literal ad length value, in seconds, reported on [ad start](/help/implementation/events/ads/ad-start.md).
