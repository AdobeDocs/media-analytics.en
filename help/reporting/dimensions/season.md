---
title: Season
description: Reports the season number for episodic content.
feature: Dimensions
role: User, Admin
---

# Season

>[!BEGINSHADEBOX]

*This page covers the **Season** reporting dimension. See [Season](/help/implementation/variables/standard-metadata/season.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Season** dimension reports the season number for episodic content. Use it alongside [Show](show.md) and [Episode](episode.md) for full episodic breakouts.

## How this dimension is populated

Season is set by the player at session start when the content is part of a series.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.season` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.season`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoseason, post_videoseason` |

## Dimension items

Each item is the literal season value reported at session start (typically a string integer such as `"1"`, `"2"`). Be consistent across episodes within the same show; the dimension does not normalize `"1"` and `"01"` to the same line item.
