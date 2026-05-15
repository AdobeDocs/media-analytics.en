---
title: Error impacted streams
description: Counts sessions in which at least one error occurred.
feature: Metrics
role: User, Admin
---

# Error impacted streams

The **Error impacted streams** metric counts sessions in which at least one error occurred (`trackError` was called or a [error](/help/implementation/events/error.md) event fired). The metric is a session-level boolean — multiple errors within the same session count as one impacted stream. For total error volume, use [Errors](/help/reporting/dimensions/errors.md).

## How this metric is calculated

The media backend sets `mediaReporting.qoeDataDetails.hasErrorImpactedStreams = true` the first time a [error](/help/implementation/events/error.md) event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.error` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.hasErrorImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.qoe.error` |
