---
title: Album
description: Reports the album the audio track belongs to.
feature: Dimensions
role: User, Admin
---

# Album

>[!BEGINSHADEBOX]

*This page covers the **Album** reporting dimension. See [Album](/help/implementation/variables/standard-metadata/album.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Album** dimension reports the album the audio track belongs to (for example, `"Pinegrove"`). Use it to roll up engagement across tracks from the same album.

## How this dimension is populated

Album is set by the player at session start for audio content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.album` when [[!UICONTROL Audio Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.album`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoaudioalbum` |
| Audience Manager | `c_contextdata.a.media.album` |

## Dimension items

Each item is the literal album title reported at session start. Two albums with the same title from different artists collapse to a single line item. Pair with the [Artist](artist.md) dimension to disambiguate.
