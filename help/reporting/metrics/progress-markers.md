---
title: Progress markers
description: Count sessions whose playhead crossed each of five fixed thresholds (10%, 25%, 50%, 75%, and 95%).
feature: Metrics
role: User, Admin
---

# Progress markers

The **Progress markers** are five separate metrics that count sessions whose playhead crossed each of five fixed thresholds (10%, 25%, 50%, 75%, and 95% of the content length). Use them to chart drop-off across the content runtime; pair with [Content starts](content-starts.md) to compute the share of started sessions that reached each milestone.

Each marker fires once per session and is not retriggered on seek-back. Skipped markers when seeking forward are not counted (for example, a viewer who jumps from 5% to 60% triggers the 10%, 25%, and 50% markers all at once).

## How each marker is calculated

The media backend evaluates the reported playhead against [Content length](../dimensions/content-length.md) after each event. When the playhead first crosses a threshold, the corresponding flag is set for the rest of the session. All five markers are reported on the close call. Sessions that never produce a play event on main content (such as [Drops before start](/help/reporting/metrics/drops-before-start.md)) never advance the playhead past any threshold, so no markers are set.

>[!IMPORTANT]
>
>Progress markers require a non-zero [Content length](/help/reporting/dimensions/content-length.md) and accurate playhead reporting. If content length is unset, zero, or wrong, markers can fire at the wrong time or not at all.

### 10% progress marker {#progress-10}

Fires when the playhead first reaches 10% of Content length.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.progress10` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasProgress10`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.progress10` |

### 25% progress marker {#progress-25}

Fires when the playhead first reaches 25% of Content length.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.progress25` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasProgress25`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.progress25` |

### 50% progress marker {#progress-50}

Fires when the playhead first reaches 50% of Content length.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.progress50` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasProgress50`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.progress50` |

### 75% progress marker {#progress-75}

Fires when the playhead first reaches 75% of Content length.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.progress75` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasProgress75`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.progress75` |

### 95% progress marker {#progress-95}

Fires when the playhead first reaches 95% of Content length.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.progress95` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.hasProgress95`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `event_list`, `post_event_list` (see [`event.tsv`](https://experienceleague.adobe.com/en/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-contents#lookup-files) lookup) |
| Audience Manager | `c_contextdata.a.media.progress95` |
