---
title: Creative URL
description: Reports the asset URL of each ad creative.
feature: Dimensions
role: User, Admin
---

# Creative URL

>[!BEGINSHADEBOX]

*This page covers the **Creative URL** reporting dimension. See [Creative URL](/help/implementation/variables/ads/creative-url.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Creative URL** dimension reports the asset URL of each ad creative. Use the dimension when the URL itself is meaningful for analysis (for example, distinguishing CDN paths or creative versions).

## How this dimension is populated

Creative URL is set by the player on every [ad start](/help/implementation/events/ads/ad-start.md) event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.creativeURL` to an eVar. |
| Customer Journey Analytics | [`xdm.mediaReporting.advertisingDetails.creativeURL`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.ad.creativeURL` to) |
| Audience Manager | `c_contextdata.a.media.ad.creativeURL` |

## Dimension items

Each item is the literal URL string reported on [ad start](/help/implementation/events/ads/ad-start.md).
