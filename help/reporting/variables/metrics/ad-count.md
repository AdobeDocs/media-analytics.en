---
title: Ad count
description: Ad count reports the number of ads that started during a session.
feature: Metrics
role: User, Admin
---

# Ad count

The **Ad count** metric reports the number of ads that started during a session. Use it to understand ad load by content, channel, or stream type. For ad start counts pivoted by ad dimensions (advertiser, campaign, creative), use the Ad starts metric available when the Ads variable category is enabled.

## How this metric is calculated

The media backend increments `mediaReporting.sessionDetails.adCount` on every `media.adStart` event received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.adCount` to a custom event. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.adCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (the custom event that your processing rule maps `a.media.adCount` to; see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
