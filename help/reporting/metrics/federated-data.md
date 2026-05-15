---
title: Federated data
description: Counts sessions received via a federated data share rather than a customer's own implementation.
feature: Metrics
role: User, Admin
---

# Federated data

>[!AVAILABILITY]
>
>The Federated Analytics service is available only when using streaming media features with Adobe Analytics. Federated Analytics is not available in Customer Journey Analytics.

The **Federated data** metric counts sessions that were received via a federated data share rather than from your own implementation. Use it to measure the volume of partner-shared sessions and compare engagement, completion, or quality against first-party sessions.

See the [Federated Media](/help/use-cases/federated-media.md) use case for more information.

>[!TIP]
>
>If you want to use federated data as a dimension, create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps the `a.media.federated` context data variable to an eVar.

## How this metric is calculated

The media backend sets `mediaReporting.sessionDetails.isFederated = true` when the session arrives over a federated channel. The metric increments once per qualifying session and is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.federated` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.isFederated`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.federated` |
