---
title: Media feed type
description: Reports the broadcast feed (for example, East-HD or West-SD) when the same content is delivered via multiple feeds.
feature: Dimensions
role: User, Admin
---

# Media feed type

>[!BEGINSHADEBOX]

*This page covers the **Media feed type** reporting dimension. See [Media feed type](/help/implementation/variables/standard-metadata/media-feed-type.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Media feed type** dimension reports the broadcast feed for each session (for example, `"East-HD"`, `"West-SD"`, or `"4K"`). Use it when the same content is delivered through multiple regional or quality feeds and engagement needs to be reported per feed.

## How this dimension is populated

Media feed type is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.feed` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.feed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videofeedtype`, `post_videofeedtype` |
| Audience Manager | `c_contextdata.a.media.feed` |

## Dimension items

Each item is the literal feed value reported at session start. Use a stable set of feed identifiers per regional or quality split.
