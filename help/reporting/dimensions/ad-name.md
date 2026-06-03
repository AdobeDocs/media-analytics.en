---
title: Ad name
description: Reports the human-readable title of each ad.
feature: Dimensions
role: User, Admin
---

# Ad name

>[!BEGINSHADEBOX]

*This page covers the **Ad name** reporting dimension. See [Ad name](/help/implementation/variables/ads/ad-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad name** dimension reports the human-readable title of each ad.

## How this dimension is populated

Ad name is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.friendlyName` when [[!UICONTROL Media Ads]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadname`, `post_videoadname` |
| Audience Manager | `c_contextdata.a.media.ad.friendlyName` |

In Adobe Analytics, this dimension appears two ways: as **Ad name (variable)** (collected directly from `a.media.ad.friendlyName`) and as **Ad name** (a classification derived from the [Ad](ad.md) dimension). If you use the classification, you are responsible for populating and maintaining its values using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). Using **Ad name (variable)** requires no classification maintenance, but you lose the guaranteed 1:1 relationship between the ad name and the parent [Ad](ad.md) dimension. Use whichever component your implementation workflow best supports.

## Dimension items

Each item is the literal ad title reported on [ad start](/help/implementation/events/ads/ad-start.md) (for example, `"Ford F-150"`).
