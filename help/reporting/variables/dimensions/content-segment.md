---
title: Content segment
description: The Content segment dimension reports the playhead range viewed during a session, in minutes.
feature: Dimensions
role: User, Admin
---

# Content segment

The **Content segment** dimension reports the playhead range viewed during a session, in minutes (for example, `[0-5]` for minutes 0 through 5). The backend computes the segment from the minimum and maximum playhead values reported during playback. Use it alongside the [Content segment views](/help/reporting/variables/metrics/content-segment-views.md) metric to analyze which portions of long-form content viewers actually consume.

## How this dimension is populated

Content segment is computed by the media backend from the playhead values reported in the session's events. It is not set by the client. The value reported is derived from the playhead values seen during playback.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.segment` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.segment`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videosegment, post_videosegment` |

>[!IMPORTANT]
>
>If the playhead is not reported correctly during the session, the computed segment may be inaccurate. For live streams, segment is computed from the relative playhead values seen during the session.

## Dimension items

Each item is a string range covering the playhead values seen during a session (for example, `[0-5]`, `[5-10]`, `[10-15]`). The granularity is fixed at five minutes.
