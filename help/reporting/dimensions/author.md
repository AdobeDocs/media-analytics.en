---
title: Author
description: Reports the author of the content. Primarily used for audiobooks.
feature: Dimensions
role: User, Admin
---

# Author

>[!BEGINSHADEBOX]

*This page covers the **Author** reporting dimension. See [Author](/help/implementation/variables/standard-metadata/author.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Author** dimension reports the author of the content (for example, `"Eleanor Clementine"`). Primarily used for audiobooks, but also valid for podcasts whose host or producer is the relevant attribution.

## How this dimension is populated

Author is set by the player at session start for audio content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.author` when [[!UICONTROL Audio Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.author`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoaudioauthor` |
| Audience Manager | `c_contextdata.a.media.author` |

## Dimension items

Each item is the literal author name reported at session start.
