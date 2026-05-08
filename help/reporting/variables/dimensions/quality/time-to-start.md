---
title: Time to start (dimension)
description: The Time to start dimension reports the elapsed time before the first frame rendered.
feature: Dimensions
role: User, Admin
---

# Time to start (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Time to start** dimension. Adobe Analytics auto-populates a paired [Time to start (metric)](/help/reporting/variables/metrics/quality/time-to-start.md) from the same `a.media.qoe.timeToStart` context data variable. Customer Journey Analytics exposes a single `mediaReporting.qoeDataDetails.timeToStart` field that you can use as either a dimension or a metric. See [Time to start](/help/implementation/variables/quality/time-to-start.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Time to start** dimension reports the elapsed time between session start and the first frame rendering. Use the dimension to break out engagement by startup-time bucket. Adobe stores the value in seconds and converts at ingest from the milliseconds the player reports.

## How this dimension is populated

The player sets `timeToStart` on the QoE object before session start fires. The backend reports the value on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.timeToStart` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.timeToStart`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoetimetostartevar` |

## Dimension items

Each item is the literal startup-time value reported on the close call.
