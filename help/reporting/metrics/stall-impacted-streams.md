---
title: Stall impacted streams
description: Counts sessions in which at least one stall occurred during playback.
feature: Metrics
role: User, Admin
---

# Stall impacted streams

The **Stall impacted streams** metric counts sessions in which at least one stall occurred during playback. The metric is a session-level boolean — multiple stalls within the same session count as one impacted stream. For total stall volume, use [Stall events](stall-events.md).

## How this metric is calculated

The media backend sets this flag when no playhead movement is recorded on main content for at least three consecutive events during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.qoe.stall` to a custom event. |
| Customer Journey Analytics | [`xdm.mediaReporting.qoeDataDetails.hasStallImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (the custom event that your processing rule maps `a.media.qoe.stall` to; see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.qoe.stall` |
