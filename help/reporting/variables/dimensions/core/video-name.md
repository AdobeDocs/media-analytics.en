---
title: Video name
description: The Video name dimension is a classification of Content (ID) that surfaces the human-readable title.
feature: Dimensions
role: User, Admin
---

# Video name

>[!BEGINSHADEBOX]

*This page covers the **Video name (classification)** dimension. See [Content name (dimension)](content-name.md) for the dimension and for Customer Journey Analytics use. See [Content name](/help/implementation/variables/core/content-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Video name (classification)** dimension is an Adobe Analytics classification of the Content (ID) dimension that surfaces the human-readable title for each content ID. Adobe automatically populates it from the latest [Content name (dimension)](content-name.md) value reported for each content ID; you can also override the values via classification files. Customer Journey Analytics does not use this classification; use the [Content name (dimension)](content-name.md) dimension directly.

## How this dimension is populated

Adobe Analytics derives Video name from the latest content name (`a.media.friendlyName` context data, `mediaCollection.sessionDetails.friendlyName` XDM field) reported for each content ID.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Content (ID) dimension — Adobe automatically populates the classification from the latest `a.media.friendlyName` value reported for each content ID. |
| Customer Journey Analytics | Use [Content name (dimension)](content-name.md) directly. |
| Data feeds | N/A |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is a human-readable title (for example, `"Blinding Light"`) that maps to one or more Content (ID) values.
