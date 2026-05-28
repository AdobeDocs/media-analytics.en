---
title: Errors
description: Reports the count of error events per session.
feature: Dimensions
role: User, Admin
---

# Errors

>[!BEGINSHADEBOX]

*This page covers the **Errors** dimension. Adobe Analytics auto-populates a paired [Error events metric](/help/reporting/metrics/error-events.md) from the same `a.media.qoe.errorCount` context data variable. Customer Journey Analytics exposes a single `xdm.mediaReporting.qoeDataDetails.errorCount` field that you can use as either a dimension or a metric.*

>[!ENDSHADEBOX]

The **Errors** dimension reports the count of error events received during a session. Use the dimension to break out engagement by exact error count.

## How this dimension is populated

The media backend increments the count on every error reported by the player. The value is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.errorCount` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.qoeDataDetails.errorCount`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoeerrorcountevar`, `post_videoqoeerrorcountevar` |
| Audience Manager | `c_contextdata.a.media.qoe.errorCount` |

## Dimension items

Each item is the literal error-count value reported on the close call. For session-level boolean reporting (whether any error occurred at all), use [Error impacted streams](/help/reporting/metrics/error-impacted-streams.md). For unique error IDs, use [External error IDs](external-error-ids.md) and [Player SDK error IDs](player-sdk-error-ids.md).

>[!NOTE]
>
>If you use the legacy Heartbeat SDK (Media SDK 1.5.x–2.x), error IDs generated internally by the SDK are automatically collected under context data key `a.media.qoe.mediaSdkErrors` and accessible in Adobe Analytics via a custom processing rule. The Audience Manager trait is `c_contextdata.a.media.qoe.mediaSdkErrors`. This field is not applicable to Media Collection API or Media Edge API implementations.
