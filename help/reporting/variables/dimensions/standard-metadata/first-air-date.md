---
title: First air date
description: The First air date dimension reports the date the content first aired on television.
feature: Dimensions
role: User, Admin
---

# First air date

>[!BEGINSHADEBOX]

*This page covers the **First air date** reporting dimension. See [First air date](/help/implementation/variables/standard-metadata/first-air-date.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **First air date** dimension reports the date the content first aired on television. In Adobe Analytics it is a classification of Content (ID); in Customer Journey Analytics it is a discrete dimension. Use it to separate engagement on new releases from engagement on older content.

## How this dimension is populated

First air date is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Content (ID) dimension — Adobe automatically populates the classification from the latest `a.media.airDate` value reported for each content ID. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.firstAirDate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal date string reported at session start. Use a consistent format across implementations. Adobe recommends `YYYY-MM-DD`.
