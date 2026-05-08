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

The **Content rating** dimension reports the audience rating for each session. In Adobe Analytics it is a classification of Content (ID); in Customer Journey Analytics it is a discrete dimension. Use it to compare engagement and ad load across rating tiers.

## How this dimension is populated

Content rating is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Content (ID) dimension — Adobe automatically populates the classification from the latest `a.media.rating` value reported for each content ID. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.rating`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal rating value reported at session start (for example, `"TVY"`, `"TVG"`, `"TVPG"`, `"TVMA"`). Stick to a fixed set of values per rating system to avoid fragmenting line items.
