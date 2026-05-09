---
title: Content segment views
description: Content segment views counts segments in which active main-content playback occurred.
feature: Metrics
role: User, Admin
---

# Content segment views

The **Content segment views** metric counts five-minute content segments in which active main-content playback occurred. The metric confirms that the viewer played content in that segment rather than just loading or buffering. Pair it with the [Content segment](/help/reporting/variables/dimensions/content-segment.md) dimension to break down which portions of long-form content viewers actually consumed.

## How this metric is calculated

The media backend sets `mediaReporting.sessionDetails.hasSegmentView = true` for any close call that covers a segment in which at least one `media.play` event for main content was received. The metric is reported on the close call. On the Media Edge API path, segment views fire under the same condition as Content starts. Both require a `media.play` on main content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.segmentView` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasSegmentView`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
