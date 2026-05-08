---
title: Ad length (classification)
description: The Ad length classification groups ads by duration. It is automatically derived from the Ad length variable.
feature: Dimensions
role: User, Admin
---

# Ad length (classification)

>[!BEGINSHADEBOX]

*This page covers the **Ad length (classification)** dimension. See [Ad length (dimension)](ad-length.md) for the dimension and for Customer Journey Analytics use. See [Ad length](/help/implementation/variables/ads/ad-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad length (classification)** dimension is an Adobe Analytics classification of the Ad dimension that groups ads by duration. Adobe automatically populates it from the latest [Ad length (dimension)](ad-length.md) value reported for each ad. Override or rebucket the values via classification files (for example, to map raw seconds into Short / Medium / Long ranges). Customer Journey Analytics does not use this classification; use the [Ad length (dimension)](ad-length.md) dimension directly.

## How this dimension is populated

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Ad dimension — Adobe automatically populates the classification from the latest `a.media.ad.length` value reported for each ad. |
| Customer Journey Analytics | Use [Ad length (dimension)](ad-length.md) directly. |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is an ad length value or a classification bucket loaded via a [classification file](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/classifications-overview).
