---
title: Label
description: Reports the record label that released the audio content.
feature: Dimensions
role: User, Admin
---

# Label

>[!BEGINSHADEBOX]

*This page covers the **Label** reporting dimension. See [Label](/help/implementation/variables/standard-metadata/label.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Label** dimension reports the record label that released the audio content (for example, `"Capitol Records"`). Use it to compare engagement across labels in a music or podcast catalog.

## How this dimension is populated

Label is set by the player at session start for audio content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.label` when [[!UICONTROL Audio Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.label`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoaudiolabel` |
| Audience Manager | `c_contextdata.a.media.label` |

## Dimension items

Each item is the literal label name reported at session start. Use a stable, canonical name per label so engagement does not fragment across spelling or imprint variants.
