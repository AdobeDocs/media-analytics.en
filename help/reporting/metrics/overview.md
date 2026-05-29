---
title: Streaming media metrics overview
description: Learn how streaming media metrics are calculated and organized across Adobe Analytics and Customer Journey Analytics.
feature: Metrics
role: User, Admin
---

# Streaming media metrics overview

Metrics in Streaming Media Analytics are event-driven counts and durations computed by the media backend. The media player sends events such as session start, play, ping, and ad start; the media backend processes those events and finalizes metric values on the session close call.

## How metrics are calculated

Streaming media metrics follow four main calculation patterns:

* **Event-triggered flags**: Set the first time a qualifying event arrives in a session. A [`play`](/help/implementation/events/playback/play.md) event for main content sets the [[!UICONTROL Content starts]](content-starts.md) flag; an [`adStart`](/help/implementation/events/ads/ad-start.md) event sets [[!UICONTROL Ad starts]](ad-starts.md). The flag is reported once per session on the close call, not per event.

* **Accumulated durations**: Sums the intervals between ping events while a particular playback state is active. [[!UICONTROL Content time spent]](content-time-spent.md) accumulates while main content is playing; [[!UICONTROL Ad time spent]](ad-time-spent.md) accumulates while an ad is playing. Adobe's recommended ping interval is 10 seconds for main content and 1 second during ads, so time spent metrics can only be as granular as your implementation's ping interval.

* **Event counts**: Track total occurrences within the session. Quality metrics such as [[!UICONTROL Buffer events]](buffer-events.md), [[!UICONTROL Bitrate changes]](bitrate-changes.md), [[!UICONTROL Error events]](error-events.md), and [[!UICONTROL Pause events]](pause-events.md) count every occurrence, not just the first.

* **Impacted streams**: Session-level flags set to 1 if the corresponding event happened at any time during the session, regardless of how many times. Use these metrics to measure reach, while using the event count metric to measure severity. For example, you can use [[!UICONTROL Buffer impacted streams]](buffer-impacted-streams.md) to determine the proportion of sessions that were impacted by buffering across all playback sessions.

## Availability by reporting system

| Reporting system | How metrics arrive |
| --- | --- |
| Adobe Analytics | Populated using [Context data variables](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/contextdata). Some metrics automatically populate solution events using these context data variables, while others must be mapped to a custom event using [Processing rules](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview). Metrics that auto-populate values must have their respective [Streaming Media report suite setting](../../implementation/media-sdk/setup/media-reports-enable.md) enabled first. |
| Customer Journey Analytics | XDM fields in `xdm.mediaReporting.sessionDetails` and related nodes, sourced from any dataset that includes streaming media data. You must create each metric with the desired settings within [Data view component settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview). |
| Data Feeds | Metrics appear in the `event_list` and `post_event_list` columns as event IDs. Each feed file contains an `events.csv` file containing the lookup for all metrics, including streaming media metrics. |

>[!MORELIKETHIS]
>
>* [Events overview](/help/implementation/events/overview.md): The player events that populate metrics
>* [Variables overview](/help/implementation/variables/overview.md): The data that events carry to Adobe
>* [Dimensions overview](/help/reporting/dimensions/overview.md): The reporting dimensions that variables populate
