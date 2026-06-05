---
title: Streaming media services release notes
description: View the release notes for streaming media services.
feature: Release Notes
role: User, Admin, Developer
exl-id: ef068aa6-fdf4-4a5c-b5d0-b93ad31894e8
TQID: https://experienceleague.adobe.com/yNfosiewndKE7c-VjoVM6D3ifYlgX3eJGgYQWcBC9no
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: f73667dc-d296-4875-8975-ac3fdc3adc42
    internal-label: Dashboards
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: ac8a38fa-dec3-4581-8f64-178fde9f64e8
    internal-label: Report Builder
  - id: c77ba355-6681-41fe-b719-563d3f507fdb
    internal-label: Mobile SDK
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# Streaming media services release notes

**Last update**: June 4, 2026

## 2026

| Feature | Description | Date |
| --- | --- | --- |
| **Support schedule data** | Upload scheduled data for past live content to track viewership by program or segment. Supported content types include:<ul><li>FAST (Free Ad Supported TV) platforms</li><li>Local streams</li><li>Live sports</li></ul>See the [Upload schedule data to track live content](/help/use-cases/track-schedule-data.md) use case for more information. | Rollout starts: October 29, 2025<p>General availability: October 2026</p> |

## 2025

| Feature | Description | Date |
| --- | --- | --- |
| **`mediaTimed` XDM field deprecation** | The `mediaTimed` XDM object is deprecated in favor of `mediaReporting` field paths. Customers who implemented the Analytics source connector before May 9, 2025 must migrate their configurations. See the following migration guides for more information:<ul><li>[Migrate audiences to the new streaming media fields](/help/implementation/edge/migrate/migrate-audiences.md)</li><li>[Migrate Customer Journey Analytics to use the new streaming media fields](/help/implementation/edge/migrate/migrate-cja-setup.md)</li><li>[Migrate Data Prep for custom fields to the new streaming media fields](/help/implementation/edge/migrate/migrate-dataprep.md)</li><li>[Migrate profiles to the new streaming media fields](/help/implementation/edge/migrate/migrate-profiles.md)</li></ul> | October 2025 |

## 2024

| Feature | Description | Date |
| --- | --- | --- |
| **Web SDK support** | Send streaming media web data to Adobe Experience Platform Edge Network using the Web SDK or Web SDK tag extension, enabling a unified collection method across Platform solutions such as Customer Journey Analytics, Real-time CDP, Journey Optimizer, and Event Forwarding. See [Set up the Web SDK for streaming media](/help/implementation/edge/web-sdk.md) or [Set up the Web SDK tag extension for streaming media](/help/implementation/edge/web-sdk-tags.md) for more information. | May 29, 2024 |
| **Roku support** | Send streaming media data to Adobe Experience Platform using the Roku SDK. See [Set up Roku for streaming media](/help/implementation/edge/roku.md) for more information. | April 12, 2024 |

## 2023

| Feature | Description | Date |
| --- | --- | --- |
| **Experience Edge support** | Implement streaming media collection using the Media Edge API or Mobile SDKs for iOS and Android.<ul><li>[Set up the Media Edge API for streaming media](/help/implementation/edge/media-edge-api.md)</li><li>[Set up iOS for streaming media](/help/implementation/edge/ios.md) or [Set up iOS for streaming media with Tags](/help/implementation/edge/ios-tags.md)</li><li>[Set up Android for streaming media](/help/implementation/edge/android.md) or [Set up Android for streaming media with Tags](/help/implementation/edge/android-tags.md)</li></ul> | May 12, 2023 |

## 2022

| Feature | Description | Date |
| --- | --- | --- |
| **Multiple Player State Tracking** | Use the Media Collection API to implement multiple player state tracking. [Learn more](/help/implementation/events/player-state/overview.md) | September 2022 |
| Renamed XDM fields | Renamed XDM field names for consistency:<ul><li>Audio and Video Parameters</li><li>Ad Parameters</li><li>Chapter Parameters</li><li>Player State Parameters</li><li>Quality Parameters</li></ul> | September 2022 |
| **Media Concurrent Viewer panel** | Understand where peak concurrency occurred or where drop-offs happened. Get valuable insight into the quality of content and viewer engagement, and help with troubleshooting or planning for volume and scale. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-workspace/panels/media-concurrent-viewers.html?lang=en) | August 9, 2022 |
| **Media Playback Time Spent panel** | Media Playback Time Spent provides valuable insight into viewer engagement and enables media organizations to derive deeper, more granular insights with minute-by-minute user engagement through advanced time spent analysis with day-parting capabilities. You can observe the amount of time spent viewing your media streams at a specific point in time. You can split the playback duration by different granularities, including new 5-minute, 15-minute, and 30-minute granularities. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-workspace/panels/media-playback-timespent/media-playback-time-spent.html) | August 9, 2022 |
| **Average Minute Audience** | Media Analytics customers can use the Average Minute Audience panel to better understand average content consumption. <br>Average minute audience enables comparisons of programming of any length or genre. In addition, you can compare or append the digital average minute audience to linear TV average minute metrics. This panel gives more flexibility to measure the average audience for custom time periods, as well as when the duration classification has been updated.  [Learn more](/help/reporting/workspace/average-minute-audience.md) | March 16, 2022 |

## 2021

| Feature | Description | Date |
| --- | --- | --- |
| **Media Playback Time Spent** | Adobe Streaming Media Playback Time Spent provides valuable insight into viewer engagement and enables media organizations to derive deeper, more granular insights with minute-by-minute user engagement through advanced time spent analysis with day-parting capabilities. You can observe the amount of time spent viewing your media streams at a specific point in time. You can split the playback duration by different granularities, including new 5 minute, 15 minute, and 30-minute granularities. [Learn more...](/help/reporting/workspace/media-playback-time-spent.md) | September 2021 |

## 2020

| Feature | Description | Date |
| --- | --- | --- |
| **Media Concurrent Viewer panel** | Understand where peak concurrency occurred or where drop-offs happened. Get valuable insight into the quality of content and viewer engagement, and help with troubleshooting or planning for volume and scale. [Learn more…](/help/reporting/workspace/media-concurrent-viewers-overview.md) <br><br>[Media Concurrent Viewers Panel in Analytics Workspace (tutorial)](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/analysis-workspace/using-panels/media-concurrent-viewers-panel-in-analysis-workspace.html?lang=en#analysis-workspace) | September 2020; January 2021 |
| **Supported devices and platforms** | The Media Launch Extension w/ AEP SDK now supports the following OTT devices: <div><ul><li>Apple TV (tvOS)</li><li>Fire TV (Fire OS)</li><li>Android TV</li></ul></div> | June 2020 |
