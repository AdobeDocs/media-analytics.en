---
seo-title: Media reports enablement
title: Media reports enablement
uuid: d306068d-a308-4b6e-8a72-742dda0de428
index: y
internal: n
snippet: y
---

# Media reports enablement{#media-reports-enablement}

Each report suite that collects video metrics must be configured before video data is sent.

>[!TIP]
>
>To take advantage of new capabilities, existing Video Analytics customers should re-enable video tracking for their RSIDs.

1. In [Reports & Analytics](https://my.omniture.com/login/), click  **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]** . 

1. Select the report suite(s) where you are collecting video data and click  **[!UICONTROL Edit Settings]** > **[!UICONTROL Media Management]** > **[!UICONTROL Media Reporting]** .

   ![](assets/media-reporting.png){width="400px"}

1. On the **[!UICONTROL Media Reporting]** page, enable **[!UICONTROL Media Core]**, and optionally enable **[!UICONTROL Media Ads]**, **[!UICONTROL Media Chapters]**, and **[!UICONTROL Media Quality]**.

   Media measurement includes the following modules:

    * **Media Core:** Core video measurement is used for media content. This will use Solution (or Custom) eVars to keep track of Content, Content Type, Content Player Name, and Content Channel. Solution (or Custom) events will be used for Media Initiates, Content Starts, Content Completes, and Content Time Spent. 
    * **Media Ads:** Media ad measurement is used for the measurement of ads within the video content. This will use Solution eVvars to measure Ad, Ad Player Name, Ad Pod, and Ad in Pod Position. Solution events will be used for Ad Starts, Ad Completes, Ad Time Spent, and Video Time Spent. 
    * **Media Chapters:** Video chapters measurement is used for the measurement of chapters. A chapter is a sub-division of content within a single video. This will use a Solution eVar to store the Chapter ID. Solution events will be used for Chapter Starts, Chapter Completes, and Chapter Time Spent. Additional chapter metadata of Chapter Name and Chapter Position will be provided as classifications of Chapter ID. 
    * **Media Quality:** Video quality measurement is used for measuring the quality of the content playback. This will use Solution eVars to store Time to Start, Buffer Events, Total Buffer Duration, Bitrate Switches, Average Bitrate, Errors, and Dropped Frames. Solution events will be used for Time to Start, Drops before Start, Buffer Impacted Streams, Buffer Events, Total Buffer Duration, Bitrate Change Impacted Streams, Bitrate Changes, Avg Bitrate, Error Impacted Streams, Error Events, Dropped Frame Impacted Streams, and Dropped Frames. 
    * **Video & Video Ad Metadata:** Metadata can be attached to a video and/or an ad to further describe and categorize that video/ad. Standardized video and ad metadata will be collected via solution variables and classifications. Values to include: Show, Season, Episode, Asset ID, Genre, First Air Date, First Digital Date, Content Rating, Originator, Network, Show Type, Ad Loads, MVPD, Authorized, Day Part, Media Session ID, Advertiser, Campaign ID, and Creative ID. 
    * **Audio & Audio Ad Metadata:** Metadata can be attached to audio and/or an ad to further describe and categorize that audio/ad. Standardized audio and ad metadata will be collected via solution variables and classifications. Values to include: Artist, Album, Label, Author, Publisher, Station, Show, Season, Episode, Asset ID, Genre, First Air Date, First Digital Date, Content Rating, Originator, Show Type, Ad Loads, Day Part, Media Session ID, Advertiser, Campaign ID, and Creative ID.

   Enabling each module reserves a set of variables and creates a new set of reports. With the exception of Quality, there will be no data in reports unless the corresponding implementation has been completed. Implementing the Core module also implements the Quality module if you enable it.

   If you are not yet tracking ads, chapters, or playback quality, you can enable additional options at any time. 

1. Click **[!UICONTROL Save]**.

   If this report suite is already configured to collect media data, after you click **[!UICONTROL Save]**, an additional configuration page is displayed. If you see the [!UICONTROL Media Core measurement] page, continue to the next step. 

1. (Conditional) On the [!UICONTROL Media Core measurement] page, select to continue using custom variables or to use solution variables. 

   | Option | Description |
   | --- | --- |
   | Continue using custom variables.  | <ul> <li> **Pros:** Content trending continues to work after migration.  </li> <li> **Cons:** Requires you to keep two custom eVars and three custom events allocated to video. You regain use of one custom eVar and one custom event.  </li> </ul> To continue using custom variables: <ol> <li>Select Use Custom Variables , then click Save .  </li> <li>When prompted, map your current custom eVars and events and then click Save : </li> </ol> |
   | Migrate to solution variables.  | <ul> <li> **Pros:** You regain use of three custom eVars and four custom events.  </li> <li> **Cons:** You lose **all** historical trending and comparison for media reports. This means that you cannot trend content views or content time played for any dates before you migrated to heartbeats.  </li> </ul> Restriction:  Do not migrate to solution variables unless you are certain that you do not want to preserve this trending.  All customers should use solution variables and processing rules to put media data into existing props and eVars, only if they need to preserve historical continuity.  To migrate to solution variables: <ol> <li>Select Use Solution Variables and click Save .  </li> </ol> | 
   
   >[!IMPORTANT] 
   >Migrating to solution variables causes you to lose **all** historical trending and comparison for media reports.  
