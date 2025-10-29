---
title: Streaming media services release notes
description: View the release notes for streaming media services release notes.
feature: Release Notes
role: User, Admin, Data Engineer
exl-id: ef068aa6-fdf4-4a5c-b5d0-b93ad31894e8
---
# Streaming media services release notes (October 2025)

**Last update**: October 7, 2025

## Related Resources

For information about new features, fixes, and important information for administrators, see the following resources.

* [Adobe Analytics release notes](https://experienceleague.adobe.com/docs/analytics/release-notes/latest.html?lang=en)
* [Customer Journey Analytics release notes](https://experienceleague.adobe.com/docs/analytics-platform/using/releases/latest.html)
* The latest release updates for [Adobe Experience Cloud products](https://business.adobe.com/products/adobe-experience-cloud-products.html)

* [Adobe Analytics Tutorials](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/overview.html?lang=en)

## *Current Release Notes*

## New and updated features for Adobe streaming media services {#cja-features}

| Feature | Description | Targeted Date |
| ----------- | ---------- | ------- |
| **Streaming media services: Support schedule data** | You can now upload scheduled data of past live Streaming Media content to more easily and accurately track viewership.<p>The following are examples of live content that are supported with schedule data upload:</p><ul><li>FAST (Free Ad Supported TV) platforms</li><li>Local streams</li><li>Live sports</li></ul><p>Uploading schedule data allows you to track viewership data for individual programs that ran during the time you designate in the upload file. You can even gather viewership data for specific topics or program segments.</p><p>These capabilities are available regardless of how you implemented Streaming Media Collection.</p><p>Previously, it was difficult to accurately tie a given session to specific programs when analyzing live content, and it wasn't possible to tie a given session to individual topics or program segments.</p><p>For more information, see [Upload schedule data to track live content](https://experienceleague.adobe.com/en/docs/media-analytics/using/media-use-cases/track-schedule-data)</p>| Rollout starts: October 29, 2025<p>General availability: First half of 2026</p><p>(Originally planned for general availability on October 29, 2025)</p> |
| Updated XDM fields for collecting streaming media data into Adobe Experience Platform | When collecting streaming media data into Adobe Experience Platform, the XDM field paths shown under the heading of "XDM Field Path" of the Streaming Media parameters documentation should no longer be used. Instead, customers who implemented the Analytics source connector to collect streaming media data into Platform before May 9, 2025 must migrate their existing configurations to the mediaReporting field paths, as shown under the heading of "Reporting XDM Field Path" of the Streaming Media parameters documentation.<p> These field paths are found on the following pages and are marked as "Deprecated": [Audio and video parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters), [Ad parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/ad-parameters), [Chapter parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/chapter-parameters), [Player state parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/player-state-parameters), and [Quality parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/quality-parameters). (No action is required for customers who implement the Analytics source connector after May 9, 2025, and are already using only mediaReporting XDM paths.)</p><p>Data ingestion on the deprecated XDM field paths will continue until the end of October 2025. After that time, deprecated field paths will be fully removed and no longer visible in the Adobe Experience Platform Schema UI, and data will be sent only using the mediaReporting field paths.</p><p>For more information, see [Migrate an Analytics Source Connector implementation to updated XDM Streaming Media fields](/help/use-cases/xdm-updates/updated-xdm-fields.md).</p><p>Please contact your Adobe Consulting Services or Account team for migration support. </p> | October 2025 |
| Send web data to Adobe Experience Platform Edge Network with the Web SDK | You can now [use the Adobe Experience Platform Web SDK to send streaming media web data to Adobe Experience Platform Edge Network](/help/implementation/edge/edge-web-sdk.md), allowing you to build more personalized campaigns and provide more personalized content, resulting in more tracking data to report on.<p>This enhancement provides a unified collection method for web implementations across all Platform solutions, such as Customer Journey Analytics, RT-CDP, AJO, and Event Forwarding. Previously, the only way to send streaming media web data to Edge Network was by using the Media Edge API. | May 29, 2024 |
| Send Roku data to Adobe Experience Platform Edge | Now when [installing the Customer Journey Analytics Streaming Media Collection with Experience Platform Edge](/help/implementation/edge/implementation-edge.md), you can use the Adobe Experience Platform Roku SDK to send streaming media data to Adobe Experience Platform. | April 12, 2024 |
| Media Collection: Integration with Experience Edge (API and Mobile SDK) | You can now use the Experience Edge API and Mobile SDK to implement the Customer Journey Analytics Streaming Media Collection, allowing you to build more personalized campaigns and provide more personalized content, resulting in more tracking data to report on.<p>This enhancement provides a unified collection method across all solutions, such as Customer Journey Analytics reporting, RT-CDP, AJO, and Event Forwarding.  [Learn more](/help/implementation/edge/implementation-edge.md) | May 12, 2023 |
| Media Concurrent Viewer panel  | Understand where peak concurrency occurred or where drop-offs happened. Get valuable insight into the quality of content and viewer engagement, and help with troubleshooting or planning for volume and scale. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-workspace/panels/media-concurrent-viewers.html?lang=en) |  August 9, 2022 |
| Media Playback Time Spent panel  |  Media Playback Time Spent provides valuable insight into viewer engagement and enables media organizations to derive deeper, more granular insights with minute-by-minute user engagement through advanced time spent analysis with day-parting capabilities. You can observe the amount of time spent viewing your media streams at a specific point in time. You can split the playback duration by different granularities, including new 5-minute, 15-minute, and 30-minute granularities. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-workspace/panels/media-playback-timespent/media-playback-time-spent.html) |  August 9, 2022 |
| Share annotations in Mobile scorecards | You can display annotations that are created in Workspace—in Mobile Scorecards. This allows you to share contextual data nuances and insights about your organization and campaigns directly within Mobile Scorecard projects, viewable in the Analytics dashboards mobile app. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/annotations/mobile-annotations.html?lang=en) | June 15, 2022 |
| Report Builder for Customer Journey Analytics updates | Includes features such as scheduling and data block manager. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-reportbuilder/manage-reportbuilder.html) | May 18, 2022 |
| Annotations in Workspace | Annotations in Workspace enable you to effectively communicate contextual data nuances and insights to your organization. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/annotations/overview.html) | Gradual rollout starts March 23, 2022 |
| Mobile scorecard project preview mode | Launch a preview of how your mobile scorecard will look in the Analytics dashboards app, directly from the scorecard builder. The preview mode allows users to interact with filters and charts in the same way they would in the app, allowing them to preview the experience before they save and share the scorecard. Users can also use the device picker in preview mode to see how their scorecard will look on different devices. [Learn more](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dashboards/create-scorecard.html#preview) | February 16, 2022 |


## New and updated features for Adobe streaming media services {#sm-features}

| Feature | Description | Targeted Date |
| ----------- | ---------- | ------- |
| Multiple Player State Tracking | Use the Media Collection API to implement multiple player state tracking. [Learn more](https://experienceleague.adobe.com/docs/media-analytics/using/player-state-tracking/multiple-player-states.html) | September 2022 |
| Renamed XDM fields | Renamed XDM field names for consistency:<br>* Audio and Video Parameters<br>* Ad Parameters<br>* Chapter Parameters<br>* Player State Parameters<br>* Quality Parameters | September 2022 |
| Device Co-op reference| Removed reference to Adobe Experience Cloud Device Co-op and the Experience Cloud ID service requirement. | August 2022 |
| Updated field names and XDM paths for collection and reporting | Updated the following:<br>* Audio and Video Parameters<br>* Ad Parameters<br>* Chapter Parameters<br>* Player State Parameters<br>* Quality Parameters | August 2022 |
| Average Minute Audience | Media Analytics customers can use the Average Minute Audience panel to better understand average content consumption. <br>Average minute audience enables comparisons of programming of any length or genre. In addition, you can compare or append the digital average minute audience to linear TV average minute metrics. This panel gives more flexibility to measure the average audience for custom time periods, as well as when the duration classification has been updated.  [Learn more](https://experienceleague.adobe.com/docs/media-analytics/using/media-reports/average-minute-audience.html?lang=en) |  March 16, 2022 |
| Media Playback Time Spent Panel | Learn how the Media Playback Time Spent Panel enables media users to understand their viewership by the amount of time viewed during the day over a chosen granularity. <br>[Media Playback Time Spent Panel (tutorial)](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/media-analytics/measuring-media-analytics/media-playback-time-spent-panel.html?lang=en) | January 2022 |


## *Previous Release Notes*

| Feature | Descripton | Targeted or Updated Date  |
| ----------- | ---------- | -------------- |
| Media Playback Time Spent | Adobe Streaming Media Playback Time Spent provides valuable insight into viewer engagement and enables media organizations to derive deeper, more granular insights with minute-by-minute user engagement through advanced time spent analysis with day-parting capabilities. You can observe the amount of time spent viewing your media streams at a specific point in time. You can split the playback duration by different granularities, including new 5 minute, 15 minute, and 30-minute granularities. [Learn more...](/help/reporting/workspace/media-playback-time-spent.md) | September 2021 |
| Media Concurrent Viewer panel in Analytics Workspace| Understand where peak concurrency occurred or where drop-offs happened. Get valuable insight into the quality of content and viewer engagement, and help with troubleshooting or planning for volume and scale. [Learn more…](/help/reporting/workspace/media-concurrent-viewers-overview.md) <br><br>[Media Concurrent Viewers Panel in Analytics Workspace (tutorial)](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/analysis-workspace/using-panels/media-concurrent-viewers-panel-in-analysis-workspace.html?lang=en#analysis-workspace) | September 2020 <br><br><br>January 2021 |
| Supported devices and platforms | The Media Launch Extension w/ AEP SDK now supports the following OTT devices: <div><ul><li>Apple TV (tvOS)</li><li>Fire TV (Fire OS)</li><li>Android TV</li></ul></div> | June 2020 |


<!-- ## Important notices for [!DNL Analytics] administrators

**Updated on March 3, 2022**

| Notice | Date Added or Updated  | Description |
| ----------- | ---------- | ---------- |
| description | date | description |
| description | date | description |
| description | date | description |
| description | date | description | -->
