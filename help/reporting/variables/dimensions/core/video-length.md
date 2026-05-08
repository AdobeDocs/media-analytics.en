---
title: Video length
description: The Video length dimension is a classification of Content (ID) that groups assets by duration.
feature: Dimensions
role: User, Admin
---

# Video length

>[!BEGINSHADEBOX]

*This page covers the **Video length (classification)** dimension. See [Content length (dimension)](content-length.md) for the dimension and for Customer Journey Analytics use. See [Content length](/help/implementation/variables/core/content-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Video length (classification)** dimension is an Adobe Analytics classification of the Content (ID) dimension that groups assets by duration. Adobe automatically populates it from the latest [Content length (dimension)](content-length.md) value reported for each content ID. Override or rebucket the values via classification files (for example, to map raw seconds into Short / Medium / Long ranges). Customer Journey Analytics does not use this classification; build a derived field or lookup on `mediaReporting.sessionDetails.length` to bucket content by duration.

## How this dimension is populated

Adobe Analytics derives Video length from the latest `a.media.length` value seen for each content ID.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Content (ID) dimension — Adobe automatically populates the classification from the latest `a.media.length` value reported for each content ID. |
| Customer Journey Analytics | Build a derived field or lookup on `mediaReporting.sessionDetails.length`. |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a content length value or a classification bucket loaded via a [classification file](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/classifications-overview). Bucket values to compare engagement across short-form (under 5 min), mid-form (5–30 min), and long-form (30+ min) content.
