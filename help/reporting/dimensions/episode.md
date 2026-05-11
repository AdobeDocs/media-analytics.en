---
title: Episode
description: The Episode dimension reports the episode number within a season.
feature: Dimensions
role: User, Admin
---

# Episode

>[!BEGINSHADEBOX]

*This page covers the **Episode** reporting dimension. See [Episode](/help/implementation/variables/standard-metadata/episode.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Episode** dimension reports the episode number within a season. Use it alongside [Show](show.md) and [Season](season.md) to break out engagement at the individual episode level.

## How this dimension is populated

Episode is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.episode` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.episode`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoepisode, post_videoepisode` |

## Dimension items

Each item is the literal episode value reported at session start (typically a string integer such as `"13"`). Episode numbers alone are not unique across seasons; pair with Season for unambiguous breakouts.
