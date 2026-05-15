---
title: Show type
description: Reports the content format (full episode, preview, clip, or other).
feature: Dimensions
role: User, Admin
---

# Show type

>[!BEGINSHADEBOX]

*This page covers the **Show type** reporting dimension. See [Show type](/help/implementation/variables/standard-metadata/show-type.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Show type** dimension reports the content format using a string integer code. Use it to separate full-program viewing from short-form content like trailers and clips when measuring engagement.

## How this dimension is populated

Show type is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.type` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.showType`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoshowtype`, `post_videoshowtype` |
| Audience Manager | `c_contextdata.a.media.type` |

## Dimension items

| Value | Description |
| --- | --- |
| `0` | Full episode |
| `1` | Preview or trailer |
| `2` | Clip |
| `3` | Other |

The values are reported as strings. Custom values are accepted but will not roll up into the four built-in buckets.
