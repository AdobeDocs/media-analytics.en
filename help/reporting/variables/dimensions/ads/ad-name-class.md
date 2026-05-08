---
title: Ad name (classification)
description: The Ad name classification surfaces the human-readable ad title. It is automatically derived from the Ad name variable.
feature: Dimensions
role: User, Admin
---

# Ad name (classification)

>[!BEGINSHADEBOX]

*This page covers the **Ad name (classification)** dimension. See [Ad name (dimension)](ad-name.md) for the dimension and for Customer Journey Analytics use. See [Ad name](/help/implementation/variables/ads/ad-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad name (classification)** dimension is an Adobe Analytics classification of the Ad dimension that surfaces the human-readable title for each ad. Adobe automatically populates it from the latest [Ad name (dimension)](ad-name.md) value reported for each ad. Customer Journey Analytics does not use this classification; use the [Ad name (dimension)](ad-name.md) dimension directly.

## How this dimension is populated

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Ad dimension — Adobe automatically populates the classification from the latest `a.media.ad.friendlyName` value reported for each ad. |
| Customer Journey Analytics | Use [Ad name (dimension)](ad-name.md) directly. |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a human-readable ad title that maps to one or more Ad ID values.
