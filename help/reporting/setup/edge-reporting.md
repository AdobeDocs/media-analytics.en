---
title: Set up reporting for Edge implementations
description: Configure Customer Journey Analytics to report on streaming media data collected through the Edge Network.
feature: Streaming Media
role: User, Admin
---
# Set up reporting for Edge implementations

After you implement the Streaming Media Collection through the Edge Network, configure Customer Journey Analytics to report on the collected data. This page describes how to create a connection, a data view, and a project for streaming media.

>[!NOTE]
>
>This page covers reporting in Customer Journey Analytics, the recommended destination for Edge implementations. If your datastream sends streaming media data to Adobe Analytics instead, see [Set up reporting for Analytics-only implementations](analytics-reporting.md).

* **Prerequisites**: Complete an Edge implementation and collect some data. See the [Edge implementation overview](/help/implementation/edge/overview.md) and your chosen implementation method.

## Create a connection in Customer Journey Analytics

1. In Customer Journey Analytics, create a connection as described in [Create a connection](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html?lang=en).

   When creating the connection, the following selections are required for streaming media:

   1. Select the dataset that you created during implementation.

   1. Ensure that the **[!UICONTROL Import all new data]** setting is enabled.

1. Continue with [Create a data view in Customer Journey Analytics](#create-a-data-view-in-customer-journey-analytics).

## Create a data view in Customer Journey Analytics

1. In Customer Journey Analytics, create a data view as described in [Create or edit a data view](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/create-dataview.html?lang=en).

   1. In the **[!UICONTROL Connection]** field, select the connection that you previously created.

      It can take up to 15 minutes before a new connection is available to select.

   1. On the **[!UICONTROL Components]** tab, in the **[!UICONTROL Schema fields]** section, search for each component in the tables below and drag it into the **[!UICONTROL Metrics]** panel. If multiple fields of the same name exist, use the XDM path to confirm the correct field.

      **Main content - Content metrics**

      | Component name | XDM path |
      |----------|---------|
      | Media Starts | mediaReporting.sessionDetails.isViewed |
      | Media Segment Views | mediaReporting.sessionDetails.hasSegmentView |
      | Content Starts | mediaReporting.sessionDetails.isPlayed |
      | Content Completes | mediaReporting.sessionDetails.isCompleted |
      | Content Time Spent | mediaReporting.sessionDetails.timePlayed |
      | Media Time Spent | mediaReporting.sessionDetails.totalTimePlayed |
      | Unique Time Played | mediaReporting.sessionDetails.uniqueTimePlayed |
      | 10% Progress Marker | mediaReporting.sessionDetails.hasProgress10 |
      | Average Minute Audience | mediaReporting.sessionDetails.averageMinuteAudience |

      **Chapter & Ads - Chapter & Ads metrics**

      | Component name | XDM path |
      |----------|---------|
      | Chapter Started | mediaReporting.chapterDetails.isStarted |
      | Chapter Completed | mediaReporting.chapterDetails.isCompleted |
      | Chapter Time Played | mediaReporting.chapterDetails.timePlayed |
      | Ad Started | mediaReporting.advertisingDetails.isStarted |
      | Ad Completed | mediaReporting.advertisingDetails.isCompleted |
      | Ad Time Played | mediaReporting.advertisingDetails.timePlayed |

      **QoE - QoE metrics**

      | Component name | XDM path |
      |----------|---------|
      | Time To Start | mediaReporting.qoeDataDetails.timeToStart |
      | Drops Before Starts | mediaReporting.qoeDataDetails.isDroppedBeforeStart |
      | Buffer Impacted Streams | mediaReporting.qoeDataDetails.hasBufferImpactedStreams |
      | Bitrate Change Impacted Streams | mediaReporting.qoeDataDetails.hasBitrateChangeImpactedStreams |
      | Bitrate Changes | mediaReporting.qoeDataDetails.bitrateChangeCount |
      | Average Bitrate | mediaReporting.qoeDataDetails.bitrateAverage |
      | Dropped Frames | mediaReporting.qoeDataDetails.droppedFrames |
      | Errors | mediaReporting.qoeDataDetails.errorCount |
      | Error Impacted Streams | mediaReporting.qoeDataDetails.hasErrorImpactedStreams |
      | Dropped Frame Impacted Streams | mediaReporting.qoeDataDetails.hasDroppedFrameImpactedStreams |

      **Player state - Player state metrics**

      | Component name | XDM path |
      |----------|---------|
      | Player State Set | mediaReporting.states.isSet |
      | Player State Count | mediaReporting.states.count |
      | Player State Time | mediaReporting.states.time |

   1. Update the labels (in the **[!UICONTROL Context labels]** drop-down menu) for the components in the following table. Search for and drag any components that are not already in the metrics panel into the panel.

      | Component name | Context label |
      |---------|----------|
      | Media Session Server Timeout | Media: Seconds Since Last Call |
      | Media Time Spent | Media: Media Time Spent |
      | Total Buffer Duration | Media: Total Buffer Duration |
      | Time to Start | Media: Time To Start |
      | Total Pause Duration | Media: Total Pause Duration |

   1. To add breakdowns to your project, add the following dimensions to the **[!UICONTROL Dimensions]** panel:

      |XDM path | Component name |
      |---------|----------|
      | mediaReporting.states.name | Player State Name |
      | mediaReporting.sessionDetails.ID | Media Session ID |

      In addition to the dimensions in this table, you can add any other dimensions that you want to filter data by in your projects.

1. Select **[!UICONTROL Save and continue]** > **[!UICONTROL Save and finish]** to save your changes.

1. Continue with [Create and configure a project in Customer Journey Analytics](#create-and-configure-a-project-in-customer-journey-analytics).

## Create and configure a project in Customer Journey Analytics

1. In Customer Journey Analytics, in the **[!UICONTROL Workspace]** tab, in the **[!UICONTROL Projects]** area, select **[!UICONTROL Create project]**.

1. Select **[!UICONTROL Blank project]** > **[!UICONTROL Create]**.

1. In the new project, select the data view that you previously created.

   When creating panels in your project, you can use any components that you added to your data view.

1. Select the **Panels** icon in the left rail, then drag in the **[!UICONTROL Media concurrent viewers]** panel and the **[!UICONTROL Media playback time spent]** panel.

1. (Conditional) If you added custom metadata to your schema, set the persistence for the custom fields, as described in [Persistence component settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence) in the Customer Journey Analytics guide.

1. Share the project as described in [Share projects](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-workspace/curate-share/share-projects.html?lang=en).

   >[!NOTE]
   >
   >If the users you want to share with are not available, make sure the users have user and admin access to Customer Journey Analytics in the Adobe Admin Console.

>[!MORELIKETHIS]
>
>* [Media panels in Workspace](/help/reporting/workspace/media-concurrent-viewers-overview.md)
>* [Dimensions overview](/help/reporting/dimensions/overview.md)
>* [Metrics overview](/help/reporting/metrics/overview.md)
