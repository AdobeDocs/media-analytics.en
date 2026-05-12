---
title: Station
description: Reports the radio station name or ID for audio broadcast content.
feature: Dimensions
role: User, Admin
---

# Station

>[!BEGINSHADEBOX]

*This page covers the **Station** reporting dimension. See [Station](/help/implementation/variables/standard-metadata/station.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Station** dimension reports the radio station name or ID broadcasting the audio content (for example, `"NPR"` or `"WXYZ-FM"`). Use it to compare engagement across stations in a syndicated network.

## How this dimension is populated

Station is set by the player at session start for audio content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.station` when [[!UICONTROL Audio Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.station`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoaudiostation` |

## Dimension items

Each item is the literal station name or ID reported at session start. Use a single canonical identifier per station so engagement does not fragment across call-sign variants.
