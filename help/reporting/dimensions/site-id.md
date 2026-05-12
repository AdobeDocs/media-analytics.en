---
title: Site ID
description: Reports the ad site identifier for each ad.
feature: Dimensions
role: User, Admin
---

# Site ID

>[!BEGINSHADEBOX]

*This page covers the **Site ID** reporting dimension. See [Site ID](/help/implementation/variables/ads/site-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Site ID** dimension reports the ad site identifier (typically an ID from your ad-server platform). Use the dimension to break out engagement by ad placement site.

## How this dimension is populated

Site ID is set by the player on every `media.adStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.site` to an eVar. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.siteID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.ad.site` to) |

## Dimension items

Each item is the literal site ID value reported on `media.adStart`.
