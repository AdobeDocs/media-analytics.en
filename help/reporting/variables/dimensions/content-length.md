---
title: Content length
description: The Content length dimension reports the total duration in seconds of each media session as set at session start.
feature: Dimensions
role: User, Admin
---

# Content length

>[!BEGINSHADEBOX]

*This page covers the **Content length** reporting dimension. See [Content length](/help/implementation/variables/core/content-length.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content length** dimension reports the total duration in seconds of each media session as set at session start. It powers backend metrics including [progress markers](/help/reporting/variables/metrics/progress-markers.md) and [Average Minute Audience](/help/reporting/variables/metrics/average-minute-audience.md).

## How this dimension is populated

Content length is set by the player at session start. The reported value is the asset's full duration in seconds, not the elapsed playhead.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.length` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videolength, post_videolength` |

>[!NOTE]
>
>In Adobe Analytics, this value also automatically populates a **Video length** classification on the [Content](content.md) dimension from the same source value. Customer Journey Analytics uses this dimension directly; derived fields on `mediaReporting.sessionDetails.length` can be used for bucketing if needed. Use whichever component that your implementation workflow best supports.

>[!IMPORTANT]
>
>If content length is not set, or is not greater than zero, then progress markers and Average Minute Audience are not produced for that session. For live streams with unknown duration, set `86400`.

## Dimension items

Each item is the literal length value, in seconds, reported at session start.
