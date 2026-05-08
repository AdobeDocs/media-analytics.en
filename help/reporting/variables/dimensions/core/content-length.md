---
title: Content length (dimension)
description: The Content length dimension reports the total duration in seconds of each media session as set at session start.
feature: Dimensions
role: User, Admin
---

# Content length (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Content length (dimension)**. See [Video length (classification)](video-length.md) for the corresponding Adobe Analytics classification derived from the same source value. See [Content length](/help/implementation/variables/core/content-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content length** dimension reports the total duration in seconds of each media session as set at session start. It is the source for the [Video length (classification)](video-length.md) and powers backend metrics including [progress markers](/help/reporting/variables/metrics/core/progress-markers.md) and [Average Minute Audience](/help/reporting/variables/metrics/core/average-minute-audience.md).

## How this dimension is populated

Content length is set by the player at session start. The reported value is the asset's full duration in seconds, not the elapsed playhead.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.length` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videolength` |

>[!IMPORTANT]
>
>If content length is not set, or is not greater than zero, then progress markers and Average Minute Audience are not produced for that session. For live streams with unknown duration, set `86400`.

## Dimension items

Each item is the literal length value, in seconds, reported at session start. Group adjacent values into ranges (Short, Medium, Long) using the [Video length (classification)](video-length.md).
