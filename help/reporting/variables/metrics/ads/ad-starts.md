---
title: Ad starts
description: Ad starts counts every ad that began playing during a session.
feature: Metrics
role: User, Admin
---

# Ad starts

The **Ad starts** metric counts every ad that began playing during a session. Pair it with [Ad completes](ad-completes.md) to compute the ad completion rate, and with [Ad count](/help/reporting/variables/metrics/core/ad-count.md) for the equivalent session-level rollup.

## How this metric is calculated

The media backend sets `mediaReporting.advertisingDetails.isStarted = true` when a `media.adStart` event is received. The metric is reported on the ad start call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.view` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.isStarted`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | `videoadstart` |
