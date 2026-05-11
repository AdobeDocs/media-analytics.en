---
title: Content rating
description: The Content rating dimension reports the audience rating as defined by TV Parental Guidelines or a regional rating system.
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
| Adobe Analytics | Classification of the [Content (ID)](content.md) dimension, created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.rating`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

In Adobe Analytics, this dimension is a classification of the [Content (ID)](content.md) dimension. Adobe creates the classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [Content rating](/help/implementation/variables/standard-metadata/content-rating.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Content (ID)](content.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal rating value reported at session start (for example, `"TVY"`, `"TVG"`, `"TVPG"`, `"TVMA"`). Stick to a fixed set of values per rating system to avoid fragmenting line items.
