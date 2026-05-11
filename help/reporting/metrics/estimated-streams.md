---
title: Estimated streams
description: Estimated streams approximates the number of audio or video streams per session.
feature: Metrics
role: User, Admin
---

# Estimated streams

The **Estimated streams** metric approximates the number of audio or video streams per session, with one stream counted for every 30 minutes of total playback. It is intended for content syndication agreements and reach approximations where each 30-minute block of consumption counts as a separate "stream."

## How this metric is calculated

The media backend computes `mediaReporting.sessionDetails.estimatedStreams = FLOOR(totalTimePlayed / 1800) + 1`, where `totalTimePlayed` is [Media time spent](media-time-spent.md) in seconds. The metric is reported on the close call.

| Media time spent | Estimated streams |
| --- | --- |
| 0–29 min | 1 |
| 30–59 min | 2 |
| 60–89 min | 3 |
| 90+ min | 4+ |

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.estimatedStreams` to a custom event. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.estimatedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (the custom event that your processing rule maps `a.media.estimatedStreams` to; see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
