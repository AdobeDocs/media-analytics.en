---
title: Content player name
description: Reports which player rendered each media session.
feature: Dimensions
role: User, Admin
---

# Content player name

>[!BEGINSHADEBOX]

*This page covers the **Content player name** reporting dimension. See [Content player name](/help/implementation/variables/core/content-player-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content player name** dimension reports which player rendered each media session (for example, `HTML5 Player`, `Brightcove`, or `Roku Player`). Use it to compare engagement, completion, and quality across players in the same property.

## How this dimension is populated

Player name is set by the player at session start and persists for the duration of the session. The value is sent on every event and reported in both Adobe Analytics and Customer Journey Analytics.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.playerName` when [[!UICONTROL Media Core]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.playerName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoplayername`, `post_videoplayername` |
| Audience Manager | `c_contextdata.a.media.playerName` |

>[!IMPORTANT]
>
>If player name is not set, the dimension is unpopulated for that session. Sessions without a player name cannot be broken down by player in reporting.

## Dimension items

Each item is the literal string set at session start. Use a stable, distinct name per player so that data from different players does not collapse into a single line item.
