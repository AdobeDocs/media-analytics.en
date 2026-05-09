---
title: Genre
description: The Genre dimension reports content genre. Multi-genre content splits across line items, each receiving equal metric weight.
feature: Dimensions
role: User, Admin
---

# Genre

>[!BEGINSHADEBOX]

*This page covers the **Genre** reporting dimension. See [Genre](/help/implementation/variables/standard-metadata/genre.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Genre** dimension reports content genre. Genre is collected as a comma-delimited string and stored as a list dimension. Multi-genre content splits across separate line items, each receiving equal metric weight. Use it to compare engagement across genres without double-counting time spent on a single multi-genre asset.

## How this dimension is populated

Genre is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.genre` (stored as a list variable) when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.genreList`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) or [`mediaReporting.sessionDetails.genre`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) (Legacy) |
| Data feeds | `videogenre, post_videogenre` |

## Dimension items

Each item is a genre value. Multi-genre sessions (for example, `"Drama,Action"`) appear as two separate line items (`Drama` and `Action`), with each item receiving full credit for the session.
