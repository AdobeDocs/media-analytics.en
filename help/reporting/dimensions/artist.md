---
title: Artist
description: Reports the performing artist for audio content.
feature: Dimensions
role: User, Admin
---

# Artist

>[!BEGINSHADEBOX]

*This page covers the **Artist** reporting dimension. See [Artist](/help/implementation/variables/standard-metadata/artist.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Artist** dimension reports the performing artist for audio content (for example, `"Crested Larks"`). Use it to break out engagement on music or podcast catalogs by performer.

## How this dimension is populated

Artist is set by the player at session start for audio content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.artist` when [[!UICONTROL Audio Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.artist`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoaudioartist` |
| Audience Manager | `c_contextdata.a.media.artist` |

## Dimension items

Each item is the literal artist name reported at session start. Use a stable, canonical name per artist so data does not fragment across formatting variants.
