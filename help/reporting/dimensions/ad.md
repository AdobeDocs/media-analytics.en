---
title: Ad
description: Reports each unique ad played, keyed by the ad ID.
feature: Dimensions
role: User, Admin
---

# Ad

>[!BEGINSHADEBOX]

*This page covers the **Ad** reporting dimension. See [Ad ID](/help/implementation/variables/ads/ad-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad** dimension reports each unique ad played, keyed by the ad ID set on [ad start](/help/implementation/events/ads/ad-start.md). The dimension is the primary breakdown for ad reporting and the join key for ad-level classifications such as Ad name, Ad length, and Creative ID.

## How this dimension is populated

Ad is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event as a stable identifier for the ad.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.name` when [[!UICONTROL Media Ads]](/help/reporting/setup/analytics-reporting.md) is enabled. Persists for the duration of the visit. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.name`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoad`, `post_videoad` |
| Audience Manager | `c_contextdata.a.media.ad.name` |

>[!IMPORTANT]
>
>Ad ID is required. If it is unset or empty, the ad is dropped from streaming media ad reporting.

## Dimension items

Each item is a unique ad ID reported on [ad start](/help/implementation/events/ads/ad-start.md). Use a stable identifier per creative so the same ad rolls up to a single line item across sessions.
