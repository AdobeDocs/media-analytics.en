---
title: Content rating
description: Reports the audience rating as defined by TV Parental Guidelines or a regional rating system.
feature: Dimensions
role: User, Admin
---

# Content rating

>[!BEGINSHADEBOX]

*This page covers the **Content rating** reporting dimension. See [Content rating](/help/implementation/variables/standard-metadata/content-rating.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content rating** dimension reports the audience rating for each session. Use it to compare engagement and ad load across rating tiers.

## How this dimension is populated

Content rating is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.rating` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Content (ID)](content.md) dimension. Adobe automatically creates this classification when **[[!UICONTROL Video Metadata]](/help/reporting/setup/analytics-reporting.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.rating`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.rating` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |
| Audience Manager | `c_contextdata.a.media.rating` |

## Classification approach

Adobe creates the Content rating classification structure automatically when **[[!UICONTROL Video Metadata]](/help/reporting/setup/analytics-reporting.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each content ID and its rating. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Content rating classification name. Renaming it can cause Adobe to recreate the original classification, resulting in a duplicate.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.rating` to an eVar. This approach captures the content rating as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the content rating and the parent [Content (ID)](content.md) dimension. If your implementation sends inconsistent values for the same content ID across events, multiple ratings can appear under the same content. Updating a value only applies to data moving forward.

## Dimension items

Each item is the literal rating value reported at session start (for example, `"TVY"`, `"TVG"`, `"TVPG"`, `"TVMA"`). Stick to a fixed set of values per rating system to avoid fragmenting line items.
