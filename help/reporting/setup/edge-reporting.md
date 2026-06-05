---
title: Set up reporting for Edge implementations
description: Configure Customer Journey Analytics to report on streaming media data collected through the Edge Network.
feature: Streaming Media
role: User, Admin
---
# Set up reporting for Edge implementations

After you implement the Streaming Media Collection through the Edge Network, configure Customer Journey Analytics to report on the collected data.

>[!NOTE]
>
>This page covers reporting in Customer Journey Analytics, the recommended destination for Edge implementations. If your datastream sends streaming media data to Adobe Analytics instead, see [Set up reporting for Analytics-only implementations](analytics-reporting.md).

* **Prerequisites**: Complete an Edge implementation and collect some data. See the [Edge implementation overview](/help/implementation/edge/overview.md) and your chosen implementation method.

## Create a connection in Customer Journey Analytics

1. In Customer Journey Analytics, create a connection as described in [Create a connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection). When creating the connection, ensure that the **[!UICONTROL Import all new data]** checkbox is enabled.

## Create a data view in Customer Journey Analytics

1. In Customer Journey Analytics, create a data view as described in [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview).

   1. In the **[!UICONTROL Connection]** field, select the connection that you previously created. New connections can take up to 15 minutes to appear.

   1. On the **[!UICONTROL Components]** tab, in the **[!UICONTROL Schema fields]** section, search for each component in the table below and drag it into the appropriate **[!UICONTROL Dimensions]** or **[!UICONTROL Metrics]** panel. If multiple fields of the same name exist, use the XDM path to confirm the correct field. Apply the context label shown in the **[!UICONTROL Context labels]** drop-down in the component settings.

      | Component | Type | XDM path | Context label |
      |---|---|---|---|
      | [Content](/help/reporting/dimensions/content.md) | Dimension | `mediaReporting.sessionDetails.name` | Media: Content ID |
      | [Content name](/help/reporting/dimensions/content-name.md) | Dimension | `mediaReporting.sessionDetails.friendlyName` | Media: Video Name |
      | [Content length](/help/reporting/dimensions/content-length.md) | Dimension | `mediaReporting.sessionDetails.length` | Media: Video Length |
      | [Show](/help/reporting/dimensions/show.md) | Dimension | `mediaReporting.sessionDetails.show` | Media: Show |
      | [Season](/help/reporting/dimensions/season.md) | Dimension | `mediaReporting.sessionDetails.season` | Media: Season |
      | [Episode](/help/reporting/dimensions/episode.md) | Dimension | `mediaReporting.sessionDetails.episode` | Media: Episode |
      | Event type | Dimension | `eventType` | Media: Event Type |
      | [Content time spent](/help/reporting/metrics/content-time-spent.md) | Metric | `mediaReporting.sessionDetails.timePlayed` | Media: Content Time Spent |
      | [Media time spent](/help/reporting/metrics/media-time-spent.md) | Metric | `mediaReporting.sessionDetails.totalTimePlayed` | Media: Media Time Spent |
      | [Total pause duration](/help/reporting/metrics/total-pause-duration.md) | Metric | `mediaReporting.sessionDetails.pauseTime` | Media: Total Pause Duration |
      | [Time to start](/help/reporting/metrics/time-to-start.md) | Metric | `mediaReporting.qoeDataDetails.timeToStart` | Media: Time to Start |
      | [Total buffer duration](/help/reporting/metrics/total-buffer-duration.md) | Metric | `mediaReporting.qoeDataDetails.bufferTime` | Media: Total Buffer Duration |
      | Media session server timeout | Metric | `mediaReporting.sessionDetails.secondsSinceLastCall` | Media: Seconds Since Last Call |

      >[!IMPORTANT]
      >
      >The context labels in this table are required for the streaming media panels to function. Customer Journey Analytics uses them to automatically compute the **Concurrent viewers** and **Playback time spent** derived metrics (used by the [Media concurrent viewers](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/media-concurrent-viewers) and [Media playback time spent](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/media-playback-time-spent) panels), and to populate the reporting options in the [Media average minute audience](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/average-minute-audience-panel) panel.

      You can add any other [dimensions](/help/reporting/dimensions/overview.md) or [metrics](/help/reporting/metrics/overview.md) to your data view at this point. Each page lists the XDM path for that component.

1. Select **[!UICONTROL Save and continue]** &rarr; **[!UICONTROL Save and finish]** to save your changes.

## Create and configure a project in Customer Journey Analytics

1. In Customer Journey Analytics, in the **[!UICONTROL Workspace]** tab, in the **[!UICONTROL Projects]** area, select **[!UICONTROL Create project]**.

1. Select **[!UICONTROL Blank project]** &rarr; **[!UICONTROL Create]**.

1. In the new project, select the data view that you previously created.

   When creating panels in your project, you can use any components that you added to your data view.

1. Select the **Panels** icon in the left rail, then drag in the **[!UICONTROL Media average minute audience]**, **[!UICONTROL Media concurrent viewers]**, and **[!UICONTROL Media playback time spent]** panels.

1. (Conditional) If you added custom metadata to your schema, set the persistence for the custom fields, as described in [Persistence component settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence) in the Customer Journey Analytics guide.

1. Share the project as described in [Share projects](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-workspace/curate-share/share-projects.html?lang=en).

   >[!NOTE]
   >
   >If the users you want to share with are not available, make sure the users have user and admin access to Customer Journey Analytics in the Adobe Admin Console.

## Available media panels in Customer Journey Analytics

Analysis Workspace in Customer Journey Analytics includes three dedicated media panels for customers with the Streaming Media Collection Add-on. These panels provide pre-built visualizations for the most common streaming media reporting needs.

* **[Media average minute audience](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/average-minute-audience-panel)**: Compares average content consumption across programs of any length or genre. Supports both specific content (duration-based) and custom time period modes, and allows updating duration classifications after the fact.
* **[Media concurrent viewers](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/media-concurrent-viewers)**: Analyzes concurrent viewers over time to identify peak concurrency and drop-off points. Supports configurable granularity and series breakdown by segments, dimensions, or date ranges.
* **[Media playback time spent](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/media-playback-time-spent)**: Analyzes playback duration over time with details on peak and trough periods. Supports configurable granularity and output format (hours or minutes).

>[!MORELIKETHIS]
>
>* [Dimensions overview](/help/reporting/dimensions/overview.md)
>* [Metrics overview](/help/reporting/metrics/overview.md)
