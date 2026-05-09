---
title: Unique time played
description: Unique time played reports the seconds of distinct content viewed during a session, deduplicating seek-back replays.
feature: Metrics
role: User, Admin
---

# Unique time played

The **Unique time played** metric reports the seconds of distinct content viewed during a session, deduplicating segments that were replayed via seek-back. Compared with [Content time spent](content-time-spent.md), unique time played is lower when a viewer rewatches a portion of the same content within the same session.

## How this metric is calculated

The media backend tracks which playhead intervals have been viewed during the session and sums their union. Playing the same five-second segment twice still counts as five seconds. The metric is reported on the close call. The value is shown as `HH:MM:SS` in Analysis Workspace and in seconds in Data Feeds, Data Warehouse, and Reporting APIs.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.uniqueTimePlayed` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.uniqueTimePlayed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
