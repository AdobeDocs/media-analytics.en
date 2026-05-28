---
title: Ad in pod position
description: Reports the zero-indexed position of each ad inside its parent ad break.
feature: Dimensions
role: User, Admin
---

# Ad in pod position

>[!BEGINSHADEBOX]

*This page covers the **Ad in pod position** reporting dimension. See [Ad in pod position](/help/implementation/variables/ads/ad-in-pod-position.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad in pod position** dimension reports the zero-indexed position of each ad inside its parent ad break. The first ad in a pod is `0`, the second is `1`, and so on. Use the dimension to compare engagement and completion by position within an ad break.

## How this dimension is populated

Ad in pod position is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.podPosition` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.podPosition`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadinpod`, `post_videoadinpod` |
| Audience Manager | `c_contextdata.a.media.ad.podPosition` |

## Dimension items

Each item is the integer position value (`0`, `1`, `2`, ...) reported on [ad start](/help/implementation/events/ads/ad-start.md).
