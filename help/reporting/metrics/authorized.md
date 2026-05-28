---
title: Authorized
description: Counts sessions whose user has been authorized through Adobe Pass.
feature: Metrics
role: User, Admin
---

# Authorized

>[!BEGINSHADEBOX]

*This page covers the **Authorized** reporting metric. See [Authorized](/help/implementation/variables/standard-metadata/authorized.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Authorized** metric counts sessions whose user has been authorized through Adobe Pass or TV-Everywhere. Pair with the [MVPD](/help/reporting/dimensions/mvpd.md) dimension to break out authentication volume by provider.

## How this metric is calculated

The media backend increments the count when the player flags the session as authorized at session start. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.pass.auth` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.authorized`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.pass.auth` |
