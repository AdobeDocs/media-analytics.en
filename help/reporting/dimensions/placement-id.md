---
title: Placement ID
description: Reports the placement identifier for each ad.
feature: Dimensions
role: User, Admin
---

# Placement ID

>[!BEGINSHADEBOX]

*This page covers the **Placement ID** reporting dimension. See [Placement ID](/help/implementation/variables/ads/placement-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Placement ID** dimension reports the ad placement identifier (typically a slot or zone defined in your ad-server platform). Use the dimension to compare engagement and completion across placement slots.

## How this dimension is populated

Placement ID is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.placement` to an eVar. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.placementID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.ad.placement` to) |
| Audience Manager | `c_contextdata.a.media.ad.placement` |

## Dimension items

Each item is the literal placement value reported on [ad start](/help/implementation/events/ads/ad-start.md).
