---
title: Creative ID
description: Reports the ad creative identifier.
feature: Dimensions
role: User, Admin
---

# Creative ID

>[!BEGINSHADEBOX]

*This page covers the **Creative ID** reporting dimension. See [Creative ID](/help/implementation/variables/ads/creative-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Creative ID** dimension reports the ad creative identifier. Use the dimension to roll up engagement across ads that share a creative.

## How this dimension is populated

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.creative` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Ad](ad.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.creativeID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.ad.creative` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |
| Audience Manager | `c_contextdata.a.media.ad.creative` |

## Classification approach

Adobe creates the Creative ID classification structure automatically when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each ad ID and its creative ID. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Creative ID classification name. Renaming it can cause Adobe to recreate the original classification, resulting in a duplicate.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.creative` to an eVar. This approach captures the creative ID as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the creative ID and the parent [Ad](ad.md) dimension. If your implementation sends inconsistent values for the same ad ID across events, multiple creative IDs can appear under the same ad. Updating a value only applies to data moving forward.

## Dimension items

Each item is a unique creative ID. Use a stable identifier per creative so the same creative rolls up to a single line item across campaigns.
