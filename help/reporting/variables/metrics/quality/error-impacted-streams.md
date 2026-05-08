---
title: Error impacted streams
description: Error impacted streams counts sessions in which at least one error occurred.
feature: Metrics
role: User, Admin
---

# Error impacted streams

The **Error impacted streams** metric counts sessions in which at least one error occurred (`trackError` was called or a `media.error` event fired). The metric is a session-level boolean — multiple errors within the same session count as one impacted stream. For total error volume, use [Errors](/help/reporting/variables/dimensions/quality/errors.md).

## How this metric is calculated

The media backend sets `mediaReporting.qoeDataDetails.hasErrorImpactedStreams = true` the first time a `media.error` event is received during the session. The metric is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.error` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.hasErrorImpactedStreams`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoeerror` |
