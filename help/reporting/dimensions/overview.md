---
title: Streaming media dimensions overview
description: Learn how streaming media dimensions are populated and organized across Adobe Analytics and Customer Journey Analytics.
feature: Dimensions
role: User, Admin
---

# Streaming media dimensions overview

Dimensions in Streaming Media Analytics let you slice and filter metrics by content name, stream type, ad name, and dozens of other attributes. Most are set by the player at session start and carried through to session close.

## How dimensions are populated

Streaming media dimensions follow three main population patterns:

* **Supplied by the media player**: The source for the majority of dimensions. The player sends these values in the [Session start](/help/implementation/events/session/session-start.md) call, and the media backend attaches them to every subsequent event in the session. What the player sends at session start is what appears in reports. Examples include [[!UICONTROL Stream type]](/help/reporting/dimensions/stream-type.md), [[!UICONTROL Content name]](/help/reporting/dimensions/content-name.md), and [[!UICONTROL Content length]](/help/reporting/dimensions/content-length.md).

* **Derived values**: Dimensions that the media backend computes from accumulated playback state rather than reading a player-supplied value. [[!UICONTROL Content segment]](/help/reporting/dimensions/content-segment.md) is computed from the playhead position over the course of playback. [[!UICONTROL Media path]](/help/reporting/dimensions/media-path.md) tracks transitions between content and ad states across the session. These dimensions cannot be overridden by the player.

* **Classifications**: Optional. Instead of populating separate dimensions, you can maintain classification data using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview) (Adobe Analytics) or [Lookup datasets](https://experienceleague.adobe.com/en/docs/analytics-platform/using/compare-aa-cja/upgrade-to-cja/create-datasets/cja-upgrade-dataset-lookup) (Customer Journey Analytics).

## Availability by reporting system

| Reporting system | How dimensions arrive |
| --- | --- |
| Adobe Analytics | Populated using [Context data variables](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/contextdata). Some dimensions automatically populate dimensions using these context data variables, while others must be populated using [Processing rules](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview). Dimensions that auto-populate values must have their respective [Streaming Media report suite setting](../media-reports-enable.md) enabled first. |
| Customer Journey Analytics | XDM fields typically in `xdm.mediaReporting.sessionDetails`, sourced from any dataset that includes streaming media data. You must create each dimension with the desired settings within [Data view component settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview). |
| Data Feeds | Dimensions automatically populated have their own data feed column names (like `videostreamtype`, `videoname`, or `videolength`). Dimensions that require processing rules use `evar` column names. |
| Audience Manager | Context data forwarded from Adobe Analytics. Available only when Analytics-to-Audience Manager server-side forwarding is configured. |

>[!MORELIKETHIS]
>
>* [Metrics overview](../metrics/overview.md): Streaming media metrics reference
>* [Parameters mapping](/help/implementation/parameters-mapping.md): Complete variable-to-column-to-XDM reference
>* [Media segments](/help/reporting/segments.md): Built-in segments that use streaming media dimensions
