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
| Avg. ads per media stream | [[!UICONTROL Ad starts]](/help/reporting/metrics/ad-starts.md) per [[!UICONTROL Media starts]](/help/reporting/metrics/media-starts.md) | `[Ad starts] / [Media starts]` |
| Avg. chapters per media stream | [[!UICONTROL Chapter starts]](/help/reporting/metrics/chapter-starts.md) per [[!UICONTROL Media starts]](/help/reporting/metrics/media-starts.md) | `[Chapter starts] / [Media starts]` |
| Avg. media time spent | [[!UICONTROL Media time spent]](/help/reporting/metrics/media-time-spent.md) per [[!UICONTROL Media starts]](/help/reporting/metrics/media-starts.md) (`HH:MM:SS`) | `[Media time spent] / [Media starts]` |
| Avg. content time spent | [[!UICONTROL Content time spent]](/help/reporting/metrics/content-time-spent.md) per [[!UICONTROL Content starts]](/help/reporting/metrics/content-starts.md) (`HH:MM:SS`) | `[Content time spent] / [Content starts]` |
| Avg. ad time spent | [[!UICONTROL Ad time spent]](/help/reporting/metrics/ad-time-spent.md) per [[!UICONTROL Ad starts]](/help/reporting/metrics/ad-starts.md) (`HH:MM:SS`) | `[Ad time spent] / [Ad starts]` |
| Avg. chapter time spent | [[!UICONTROL Chapter time spent]](/help/reporting/metrics/chapter-time-spent.md) per [[!UICONTROL Chapter starts]](/help/reporting/metrics/chapter-starts.md) (`HH:MM:SS`) | `[Chapter time spent] / [Chapter starts]` |
| Media completion rate | Rate of [[!UICONTROL Content completes]](/help/reporting/metrics/content-completes.md) vs. [[!UICONTROL Media starts]](/help/reporting/metrics/media-starts.md) | `[Content completes] / [Media starts]` |
| Content completion rate | Rate of [[!UICONTROL Content completes]](/help/reporting/metrics/content-completes.md) vs. [[!UICONTROL Content starts]](/help/reporting/metrics/content-starts.md) | `[Content completes] / [Content starts]` |
| Ad completion rate | Rate of [[!UICONTROL Ad completes]](/help/reporting/metrics/ad-completes.md) vs. [[!UICONTROL Ad starts]](/help/reporting/metrics/ad-starts.md) | `[Ad completes] / [Ad starts]` |
| Chapter completion rate | Rate of [[!UICONTROL Chapter completes]](/help/reporting/metrics/chapter-completes.md) vs. [[!UICONTROL Chapter starts]](/help/reporting/metrics/chapter-starts.md) | `[Chapter completes] / [Chapter starts]` |
| Drop before start rate | Rate of [[!UICONTROL Drops before start]](/help/reporting/metrics/drops-before-start.md) vs. [[!UICONTROL Media starts]](/help/reporting/metrics/media-starts.md) | `[Drops before start] / [Media starts]` |
| Content pause duration rate | Rate of [[!UICONTROL Total pause duration]](/help/reporting/metrics/total-pause-duration.md) vs. [[!UICONTROL Content time spent]](/help/reporting/metrics/content-time-spent.md) | `[Total pause duration] / [Content time spent]` |
| Content buffer duration rate | Rate of [[!UICONTROL Total buffer duration]](/help/reporting/metrics/total-buffer-duration.md) vs. [[!UICONTROL Content time spent]](/help/reporting/metrics/content-time-spent.md) | `[Total buffer duration] / [Content time spent]` |
| Content time-to-start rate | Rate of [[!UICONTROL Time to start]](/help/reporting/metrics/time-to-start.md) vs. [[!UICONTROL Content time spent]](/help/reporting/metrics/content-time-spent.md) | `[Time to start] / [Content time spent]` |
| Ad time spent rate | Rate of [[!UICONTROL Ad time spent]](/help/reporting/metrics/ad-time-spent.md) vs. [[!UICONTROL Content time spent]](/help/reporting/metrics/content-time-spent.md) | `[Ad time spent] / [Content time spent]` |

