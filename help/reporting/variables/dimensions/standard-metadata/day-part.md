---
title: Day part
description: The Day part dimension reports the time-of-day bucket (Morning, Afternoon, Primetime, Late Night) when the content was broadcast or played.
feature: Dimensions
role: User, Admin
---

# Day part

>[!BEGINSHADEBOX]

*This page covers the **Day part** reporting dimension. See [Day part](/help/implementation/variables/standard-metadata/day-part.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Day part** dimension reports the time-of-day bucket when the content was broadcast or played. Common values are `"Morning"`, `"Afternoon"`, `"Primetime"`, and `"Late Night"`. Use it to compare engagement across dayparts independently of the viewer's local time zone.

## How this dimension is populated

Day part is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.dayPart` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.dayPart`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videodaypart` |

## Dimension items

Each item is the literal daypart label reported at session start. Use a fixed set of values across implementations to keep line items consistent.
