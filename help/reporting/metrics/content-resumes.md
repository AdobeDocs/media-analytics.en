---
title: Content resumes
description: Counts sessions that resumed a previously interrupted playback.
feature: Metrics
role: User, Admin
---

# Content resumes

>[!BEGINSHADEBOX]

*This page covers the **Content resumes** reporting metric. See [Content resumes](/help/implementation/variables/core/content-resumes.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content resumes** metric counts sessions that resumed a previously interrupted playback. It is incremented when the player flags a session as a resume on `sessionStart` (for example, after a buffer, pause, or stall exceeded 30 minutes). Use it to separate genuine new sessions from continuation sessions for the same viewer and asset.

## How this metric is calculated

The media backend sets this flag when `mediaCollection.sessionDetails.hasResume` is `true` on the [session start](/help/implementation/events/session/session-start.md) event. The player must explicitly flag the session as a resume. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.resume` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasResume`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | N/A |
