---
title: Originator
description: The Originator dimension reports the creator or production studio of the content.
feature: Dimensions
role: User, Admin
---

# Originator

>[!BEGINSHADEBOX]

*This page covers the **Originator** reporting dimension. See [Originator](/help/implementation/variables/standard-metadata/originator.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Originator** dimension reports the creator or production studio of the content (for example, `"Warner Brothers"` or `"Sony"`). Use it to compare engagement across content owners or rights holders.

## How this dimension is populated

Originator is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Content (ID) dimension — Adobe automatically populates the classification from the latest `a.media.originator` value reported for each content ID. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.originator`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal originator value reported at session start. Use a stable, distinct name per studio so engagement does not collapse across unrelated entities.
