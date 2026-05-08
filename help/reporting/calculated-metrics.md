---
title: Calculated metrics
description: Custom calculated metrics for streaming media reporting in Adobe Analytics and Customer Journey Analytics.
feature: Metrics
role: User, Admin
---

# Calculated metrics

Calculated metrics for Adobe streaming media services are custom metrics built from the standard streaming media metrics, letting you derive ratios such as average ad time spent or media completion rate without changing your implementation.

To create these calculated metrics in Analysis Workspace, see the respective calculated metrics overview in [Adobe Analytics](https://experienceleague.adobe.com/en/docs/analytics/components/calculated-metrics/cm-overview) or [Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview).

| Calculated metric | Description | Formula |
| --- | --- | --- |
| Avg. ads per media stream | Ad starts per media starts | [`Ad Starts`](/help/reporting/variables/metrics/ads/ad-starts.md) / [`Media Starts`](/help/reporting/variables/metrics/core/media-starts.md) |
| Avg. chapters per media stream | Chapter starts per media starts | [`Chapter Starts`](/help/reporting/variables/metrics/chapters/chapter-starts.md) / [`Media Starts`](/help/reporting/variables/metrics/core/media-starts.md) |
| Avg. media time spent | Total time spent per media starts (`HH:MM:SS`) | [`Media Time Spent`](/help/reporting/variables/metrics/core/media-time-spent.md) / [`Media Starts`](/help/reporting/variables/metrics/core/media-starts.md) |
| Avg. content time spent | Content time spent per content starts (`HH:MM:SS`) | [`Content Time Spent`](/help/reporting/variables/metrics/core/content-time-spent.md) / [`Content Starts`](/help/reporting/variables/metrics/core/content-starts.md) |
| Avg. ad time spent | Ad time spent per ad starts (`HH:MM:SS`) | [`Ad Time Spent`](/help/reporting/variables/metrics/ads/ad-time-spent.md) / [`Ad Starts`](/help/reporting/variables/metrics/ads/ad-starts.md) |
| Avg. chapter time spent | Chapter time spent per chapter starts (`HH:MM:SS`) | [`Chapter Time Spent`](/help/reporting/variables/metrics/chapters/chapter-time-spent.md) / [`Chapter Starts`](/help/reporting/variables/metrics/chapters/chapter-starts.md) |
| Media completion rate | Rate of content completed vs. media initiated | [`Content Completes`](/help/reporting/variables/metrics/core/content-completes.md) / [`Media Starts`](/help/reporting/variables/metrics/core/media-starts.md) |
| Content completion rate | Rate of content completed vs. content starts | [`Content Completes`](/help/reporting/variables/metrics/core/content-completes.md) / [`Content Starts`](/help/reporting/variables/metrics/core/content-starts.md) |
| Ad completion rate | Rate of ad completes vs. ad starts | [`Ad Completes`](/help/reporting/variables/metrics/ads/ad-completes.md) / [`Ad Starts`](/help/reporting/variables/metrics/ads/ad-starts.md) |
| Chapter completion rate | Rate of chapter completes vs. chapter starts | [`Chapter Completes`](/help/reporting/variables/metrics/chapters/chapter-completes.md) / [`Chapter Starts`](/help/reporting/variables/metrics/chapters/chapter-starts.md) |
| Drop before start rate | Rate of drops before start vs. media starts | [`Drops Before Start`](/help/reporting/variables/metrics/quality/drops-before-start.md) / [`Media Starts`](/help/reporting/variables/metrics/core/media-starts.md) |
| Content pause duration rate | Rate of total pause duration vs. content time spent | [`Total Pause Duration`](/help/reporting/variables/metrics/core/total-pause-duration.md) / [`Content Time Spent`](/help/reporting/variables/metrics/core/content-time-spent.md) |
| Content buffer duration rate | Rate of total buffer duration vs. content time spent | [`Total Buffer Duration`](/help/reporting/variables/metrics/quality/total-buffer-duration.md) / [`Content Time Spent`](/help/reporting/variables/metrics/core/content-time-spent.md) |
| Content time-to-start rate | Rate of time to start vs. content time spent | [`Time to Start`](/help/reporting/variables/metrics/quality/time-to-start.md) / [`Content Time Spent`](/help/reporting/variables/metrics/core/content-time-spent.md) |
| Ad time spent rate | Rate of ad time spent vs. content time spent | [`Ad Time Spent`](/help/reporting/variables/metrics/ads/ad-time-spent.md) / [`Content Time Spent`](/help/reporting/variables/metrics/core/content-time-spent.md) |
