---
title: Content channel
description: Reports the distribution station, network, or property where each session played.
feature: Dimensions
role: User, Admin
---

# Content channel

>[!BEGINSHADEBOX]

*This page covers the **Content channel** reporting dimension. See [Content channel](/help/implementation/variables/core/content-channel.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content channel** dimension reports the distribution station, network, or property where each session played. Use it to break out playback by network or section of a property.

## How this dimension is populated

Channel is set by the player at session start and persists for the duration of the session.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.channel` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.channel`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videochannel, post_videochannel` |

>[!IMPORTANT]
>
>If channel is not set, the dimension is unpopulated for that session.

## Dimension items

Each item is the literal string set at session start. Any string is accepted. Typical values are a network name, a portion of a site path, or an internal property identifier.
