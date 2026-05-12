---
title: Show
description: Reports the program or series name for video content that is part of a series.
feature: Dimensions
role: User, Admin
---

# Show

>[!BEGINSHADEBOX]

*This page covers the **Show** reporting dimension. See [Show](/help/implementation/variables/standard-metadata/show.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Show** dimension reports the program or series name. Episodes from multiple seasons roll up to the same show line item, so use it to compare engagement across the full lifetime of a series.

## How this dimension is populated

Show is set by the player at session start when the content is part of a series.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.show` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.show`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoshow, post_videoshow` |

## Dimension items

Each item is the literal show name reported at session start (for example, `"Blinding Light"`). Use stable, distinct names per show so that data does not collapse across unrelated programs that share a word.
