---
title: Media reports enablement
description: Learn about the media report suite that collects media metrics.  Follow these steps to configure media reports before media data is sent.
uuid: d306068d-a308-4b6e-8a72-742dda0de428
exl-id: 686d88a5-79b6-4936-ba9e-8f834ef330d1
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/2nLLlF-rFJUR3t-OMbcy5iqF42l-O7oLybXFGhdPyhU
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: c153fd90-23e1-4614-81d3-3cc7571227f7
    internal-label: Analysis Workspace
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: c9bb7ea6-c04f-4262-b69c-fbb8d91e3559
    internal-label: Streaming Media
  - id: e38cbddc-1633-4cd5-bed5-9f289f2a6029
    internal-label: Panels
  - id: ef60b66e-5984-4336-ba72-6d978b1b6f87
    internal-label: Report suites
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
  - id: f836f655-eebe-4b76-82bc-697955ec1ce3
    internal-label: Calculated Metrics
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
---
# Media reports enablement{#media-reports-enablement}

Each report suite that collects media metrics must be configured before media data is sent.

Advanced customers can use the media panels in Analysis Workspace only after Media Core is enabled and tracking is enabled for [Quality of Experience](/help/use-cases/track-qos/track-qos-overview.md).

>[!TIP]
>
>To take advantage of new capabilities, existing streaming media customers should re-enable media tracking for their RSIDs.

1. In [Reports & Analytics](https://my.omniture.com/login/) click **[!UICONTROL Admin > Report Suites].**
1. Select the report suite(s) where you are collecting media data and click **[!UICONTROL Edit Settings > Media Management > Media Reporting].**

    ![](assets/media-reporting.png)

1. On the **[!UICONTROL Media Reporting]** page, enable **[!UICONTROL Media Core],** and optionally enable **[!UICONTROL Media Ads],** **[!UICONTROL Media Chapters],** and **[!UICONTROL Media Quality].**

    Media measurement includes the following modules:

    * **Media Core**

       Core media measurement is used for media content. This will use Solution (or Custom) eVars to keep track of Content, Content Type, Content Player Name, and Content Channel. Solution (or Custom) events will be used for Media Starts, Content Starts, Content Completes, and Content Time Spent.

    * **Media Ads**

       Media ad measurement is used for the measurement of ads within the media content. This will use Solution eVvars to measure Ad, Ad Player Name, Ad Pod, and Ad in Pod Position. Solution events will be used for Ad Starts, Ad Completes, Ad Time Spent, and Video Time Spent.

    * **Media Chapters**

       Video chapters measurement is used for the measurement of chapters. A chapter is a sub-division of content within a single media. This will use a Solution eVar to store the Chapter ID. Solution events will be used for Chapter Starts, Chapter Completes, and Chapter Time Spent. Additional chapter metadata of Chapter Name and Chapter Position will be provided as classifications of Chapter ID.

    * **Media Quality**

       Video quality measurement is used for measuring the quality of the content playback. This will use Solution eVars to store Time to Start, Buffer Events, Total Buffer Duration, Bitrate Switches, Average Bitrate, Errors, and Dropped Frames. Solution events will be used for Time to Start, Drops before Start, Buffer Impacted Streams, Buffer Events, Total Buffer Duration, Bitrate Change Impacted Streams, Bitrate Changes, Avg Bitrate, Error Impacted Streams, Error Events, Dropped Frame Impacted Streams, and Dropped Frames.

    * **Video & Video Ad Metadata**

       Metadata can be attached to a media and/or an ad to further describe and categorize that media/ad. Standardized media and ad metadata will be collected via solution variables and classifications. Values to include: Show, Season, Episode, Asset ID, Genre, First Air Date, First Digital Date, Content Rating, Originator, Network, Show Type, Ad Loads, MVPD, Authorized, Day Part, Media Session ID, Advertiser, Campaign ID, and Creative ID.

    * **Audio & Audio Ad Metadata**

       Metadata can be attached to audio and/or an ad to further describe and categorize that audio/ad. Standardized audio and ad metadata will be collected via solution variables and classifications. Values to include: Artist, Album, Label, Author, Publisher, Station, Show, Season, Episode, Asset ID, Genre, First Air Date, First Digital Date, Content Rating, Originator, Show Type, Ad Loads, Day Part, Media Session ID, Advertiser, Campaign ID, and Creative ID.

   Enabling each module reserves a set of variables and creates a new set of reports. With the exception of Quality, there will be no data in reports unless the corresponding implementation has been completed. Implementing the Core module also implements the Quality module if you enable it.

   If you are not yet tracking ads, chapters, or playback quality, you can enable additional options at any time.

1. Click **[!UICONTROL Save].**

   If this report suite is already configured to collect media data, after you click **[!UICONTROL Save]**, an additional configuration page is displayed. If you see the **[!UICONTROL Media Core measurement]** page, continue to the next step.

1. (Conditional) On the **[!UICONTROL Media Core measurement]** page, choose to continue using custom variables or choose to use solution variables.

   | Option | Notes |
   | --- | --- |
   | Continue using custom variables | Pros and Cons:<ul> <li> **Pros:** Content trending continues to work after migration. </li> <li> **Cons:** Requires you to keep two custom eVars and three custom events allocated to media. You regain use of one custom eVar and one custom event. </li> </ul> To continue using custom variables: <ol> <li>Select **[!UICONTROL Use Custom Variables,]** then click **[!UICONTROL Save.]** </li> <li>When prompted, map your current custom eVars and events and then click **[!UICONTROL Save:]** </li> </ol> |
   | Migrate to solution variables | Pros and Cons:<ul> <li> **Pros:** You regain use of three custom eVars and four custom events. </li> <li> **Cons:** You lose **all** historical trending and comparison for media reports. This means that you cannot trend content views or content time played for any dates before you migrated to heartbeats. </li> </ul> **Restriction:**  Do not migrate to solution variables unless you are certain that you do not want to preserve this trending. All customers should use solution variables and processing rules to put media data into existing props and eVars, only if they need to preserve historical continuity. To migrate to solution variables: Select **[!UICONTROL Use Solution Variables]** and click **[!UICONTROL Save].** <br><br> IMPORTANT: Migrating to solution variables causes you to lose **all** historical trending and comparison for media reports. |

>[!IMPORTANT]
>
>Do not change the classification names for any variables listed in the streaming media variable documentation (linked from the [Streaming media services overview](/help/media-overview.md)) that are described there under Reporting/Reserved Variable as "classification". The media classifications are defined when a report suite is enabled for media tracking. From time to time, Adobe adds new properties, and when this occurs, customers must re-enable their report suites to get access to the new media properties. During the update process Adobe determines whether the classifications are enabled by checking the names of the variables. If any of them is missing, Adobe adds the missing ones again.
