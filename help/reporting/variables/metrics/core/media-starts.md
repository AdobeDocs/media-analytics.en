---
title: Media starts
description: Media starts counts every media session that began, including sessions that ended in pre-roll ads or buffering.
feature: Metrics
role: User, Admin
---

# Media starts

The **Media starts** metric counts every media session that began. It is incremented as soon as the backend receives a `media.sessionStart` event, even if the viewer drops out during pre-roll ads, buffering, or before any main content plays. Use it as the broadest top-of-funnel metric for media reporting; pair it with [Content starts](content-starts.md) to measure ad and buffer drop-off.

## How this metric is calculated

The media backend sets `mediaReporting.sessionDetails.isViewed = true` when a `media.sessionStart` event is received. The reported metric is `1` per session. Media starts is reported on the start call, not the close call. It is the only Phase 1 metric that does not wait for session close.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.view` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.isViewed`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videostart` |
