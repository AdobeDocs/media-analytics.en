---
title: Migrate audiences to the new Adobe Analytics for Streaming Media data type
description: Learn how to migrate audiences to the new Adobe Analytics for Streaming Media data type
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Media Analytics parameters mapping for Adobe Experience Platform and Customer Journey Analytics

This document provides a comprehensive list of all Media Analytics parameters utilized within Adobe Experience Platform and Customer Journey Analytics. It is intended to support the integration of data imported from Adobe Analytics to Platform via the [Analytics Source Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/analytics) or the [Analytics Source Connector for Classifications](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/classifications), mapping each parameter to its corresponding XDM field path.

## Media Analytics reserved variables

For all Media Analytics reserved variables, data ingested from Adobe Analytics into AEP until (and including) May 2025 can be found under the 'Current XDM Field Path' pointed out in the tables below.

As the Media Analytics and ADC teams are currently working toward full migration to the 'Reporting XDM Field Path', an official communication will be shared once this migration is complete and the 'Reporting XDM Field Path' is available for use.

## Streaming Media parameters

| Field name         | Current XDM Field Path (Deprecated)                                      | Reporting XDM Field Path                          | Data Type | Derived field     | Notes                                                                 |
|--------------------|---------------------------------------------------------------------------|---------------------------------------------------|-----------|-------------------|-----------------------------------------------------------------------|
| Stream Type        | media.mediaTimed.primaryAssetReference.streamType                        | mediaReporting.sessionDetails.streamType          | Dimension | Stream Type        |                                                                       |
| Content ID         | media.mediaTimed.primaryAssetReference._id                               | mediaReporting.sessionDetails.name                | Dimension | Content ID         |                                                                       |
| Content Length     | media.mediaTimed.primaryAssetReference._xmpDM.duration                   | mediaReporting.sessionDetails.length              | Dimension | Content Length     |                                                                       |
| Content Type       | media.mediaTimed.primaryAssetViewDetails.broadcastContentType            | mediaReporting.sessionDetails.contentType         | Dimension | Content Type       |                                                                       |
| Media Session ID   | media.mediaTimed.primaryAssetViewDetails._id                             | mediaReporting.sessionDetails.ID                  | Dimension | Media Session ID   |                                                                       |
| Content Player Name| media.mediaTimed.primaryAssetViewDetails.playerName                      | mediaReporting.sessionDetails.playerName          | Dimension | Content Player Name|                                                                       |
| Content Channel    | media.mediaTimed.primaryAssetViewDetails.broadcastChannel                | mediaReporting.sessionDetails.channel             | Dimension | Content Channel    |                                                                       |
| Content Segment    | media.mediaTimed.primaryAssetViewDetails.videoSegment                    | mediaReporting.sessionDetails.segment             | Dimension | Content Segment    |                                                                       |
| Content Name       | media.mediaTimed.primaryAssetReference._dc.title                         | mediaReporting.sessionDetails.friendlyName        | Dimension | Content Name       |                                                                       |
| Video Path         | *Not used in AEP/CJA*                                                     |                                                   |           |                   | Adobe Analytics specific property                                    |
| Show               | media.mediaTimed.primaryAssetReference._iptc4xmpExt.Series._iptc4xmpExt.Name | mediaReporting.sessionDetails.show            | Dimension | Show               |                                                                       |
| Season             | media.mediaTimed.primaryAssetReference._iptc4xmpExt.Season._iptc4xmpExt.Name | mediaReporting.sessionDetails.season          | Dimension | Season             |                                                                       |
| Episode            | media.mediaTimed.primaryAssetReference._iptc4xmpExt.Episode._iptc4xmpExt.Name | mediaReporting.sessionDetails.episode        | Dimension | Episode            |                                                                       |
| Genre              | media.mediaTimed.primaryAssetReference._iptc4xmpExt.Genre                | mediaReporting.sessionDetails.genreList           | Dimension | not supported      | Use mediaReporting field                                             |
| Network            | media.mediaTimed.primaryAssetViewDetails.broadcastNetwork                | mediaReporting.sessionDetails.network             | Dimension | Network            |                                                                       |
| Show Type          | media.mediaTimed.primaryAssetReference.showType                          | mediaReporting.sessionDetails.showType            | Dimension | Show Type          |                                                                       |
| MVPD               | media.mediaTimed.idp                                                     | mediaReporting.sessionDetails.mvpd                | Dimension | MVPD               |                                                                       |
| Authorized         | Not supported                                                            | mediaReporting.sessionDetails.authorized          | Dimension | Authorized         |                                                                       |
| Day Part           | Not supported                                                            | mediaReporting.sessionDetails.dayPart             | Dimension | Day Part           |                                                                       |
| Media Feed Type    | media.mediaTimed.primaryAssetViewDetails.sourceFeed                      | mediaReporting.sessionDetails.feed                | Dimension | Media Feed Type    |                                                                       |
| Artist             | media.mediaTimed.primaryAssetReference._xmpDM.artist                     | mediaReporting.sessionDetails.artist              | Dimension | Artist             |                                                                       |
| Album              | media.mediaTimed.primaryAssetReference._xmpDM.album                      | mediaReporting.sessionDetails.album               | Dimension | Album              |                                                                       |
| Label              | Not supported                                                            | mediaReporting.sessionDetails.label               | Dimension | Label              |                                                                       |
| Author             | Not supported                                                            | mediaReporting.sessionDetails.author              | Dimension | Author             |                                                                       |
| Station            | media.mediaTimed.primaryAssetReference._id3.Audio._id3.TRSN              | mediaReporting.sessionDetails.station             | Dimension | Station            |                                                                       |
| Publisher          | media.mediaTimed.primaryAssetReference._id3.Audio._id3.TPUB              | mediaReporting.sessionDetails.publisher           | Dimension | Publisher          |                                                                       |
| Media Starts           | media.mediaTimed.impressions.value                  | mediaReporting.sessionDetails.isViewed            | Metric    | Media Starts       |                                                                       |
| Content Starts         | media.mediaTimed.starts.value                       | mediaReporting.sessionDetails.isPlayed            | Metric    | Content Starts     |                                                                       |
| Content Complete       | media.mediaTimed.completes.value                    | mediaReporting.sessionDetails.isCompleted         | Metric    | Content Complete   |                                                                       |
| Content Time Spent     | media.mediaTimed.timePlayed.value                   | mediaReporting.sessionDetails.timePlayed          | Metric    | Content Time Spent |                                                                       |
| Media Time Spent       | media.mediaTimed.totalTimePlayed.value              | mediaReporting.sessionDetails.totalTimePlayed     | Metric    | Media Time Spent   |                                                                       |
| Unique Time Played     | Not supported                                       | mediaReporting.sessionDetails.uniqueTimePlayed    | Metric    | Unique Time Played |                                                                       |
| 10% Progress Marker    | media.mediaTimed.progress10.value                   | mediaReporting.sessionDetails.hasProgress10       | Metric    | 10% Progress Marker|                                                                       |
| 25% Progress Marker    | media.mediaTimed.progress25.value                   | mediaReporting.sessionDetails.hasProgress25       | Metric    | 25% Progress Marker|                                                                       |
| 50% Progress Marker    | media.mediaTimed.progress50.value                   | mediaReporting.sessionDetails.hasProgress50       | Metric    | 50% Progress Marker|                                                                       |
| 75% Progress Marker    | media.mediaTimed.progress75.value                   | mediaReporting.sessionDetails.hasProgress75       | Metric    | 75% Progress Marker|                                                                       |
| 95% Progress Marker    | media.mediaTimed.progress95.value                   | mediaReporting.sessionDetails.hasProgress95       | Metric    | 95% Progress Marker|                                                                       |
| Average Minute Audience| Not supported                                       | mediaReporting.sessionDetails.averageMinuteAudience| Metric   | Average Minute Audience|                                                                  |
| Seconds Since Last Call| media.mediaTimed.primaryAssetViewDetails.sessionTimeout | mediaReporting.sessionDetails.secondsSinceLastCall | Metric | Seconds Since Last Call|                                                              |
| Paused Impacted Streams| Not supported                                       | mediaReporting.sessionDetails.hasPauseImpactedStreams | Metric | Paused Impacted Streams | we cover mediaTimed by calculating this value from other events |
| Pause Events           | media.mediaTimed.pauses.value                       | mediaReporting.sessionDetails.pauseCount          | Metric    | Pause Events       |                                                                       |
| Total Pause Duration   | media.mediaTimed.pauseTime.value                    | mediaReporting.sessionDetails.pauseTime           | Metric    | Total Pause Duration|                                                                       |
| Content Resumes        | media.mediaTimed.resumes.value                      | mediaReporting.sessionDetails.hasResume           | Metric    | Content Resumes    |                                                                       |
| Content Segment Views  | media.mediaTimed.mediaSegmentViews.value            | mediaReporting.sessionDetails.hasSegmentView      | Metric    | Content Segment Views|                                                                     |

{style="table-layout:auto"}

## Player state parameters update

| Field name                 | Current XDM Field Path (Deprecated) | Reporting XDM Field Path         | Data Type | Derived field | Notes                                |
|----------------------------|-------------------------------------|----------------------------------|-----------|----------------|--------------------------------------|
| Streams Impacted by Player States | Not supported              | mediaReporting.states.isSet      | Metric    | not supported   | use mediaReporting field             |
| Player States Counts       | Not supported                      | mediaReporting.states.count      | Metric    | not supported   | use mediaReporting field             |
| Player States Total Duration | Not supported                    | mediaReporting.states.time       | Metric    | not supported   | use mediaReporting field             |
| Player State Name          | Not supported                      | mediaReporting.states.name       | Dimension | not supported   | use mediaReporting field             |

{style="table-layout:auto"}

## Chapter parameters

| Field name       | Current XDM Field Path (Deprecated)                          | Reporting XDM Field Path                  | Data Type | Derived field | Notes     |
|------------------|--------------------------------------------------------------|-------------------------------------------|-----------|----------------|-----------|
| Chapter          | media.mediaTimed.mediaChapter.chapterAssetReference._id     | mediaReporting.chapterDetails.ID          | Dimension | Chapter        |           |
| Chapter Start    | media.mediaTimed.mediaChapter.impressions.value              | mediaReporting.chapterDetails.isStarted   | Metric    | Chapter Start  |           |
| Chapter Complete | media.mediaTimed.mediaChapter.completes.value                | mediaReporting.chapterDetails.isCompleted | Metric    | Chapter Complete|          |
| Chapter Time Spent| media.mediaTimed.mediaChapter.timePlayed.value              | mediaReporting.chapterDetails.timePlayed  | Metric    | Chapter Time Spent|        |

{style="table-layout:auto"}

## Ad parameters

| Field name       | Current XDM Field Path (Deprecated)                          | Reporting XDM Field Path                      | Data Type | Derived field | Notes     |
|------------------|--------------------------------------------------------------|------------------------------------------------|-----------|----------------|-----------|
| Ad ID            | advertising.adAssetReference._id                             | mediaReporting.advertisingDetails.name        | Dimension | Ad ID          |           |
| Ad In Pod Position | advertising.adAssetViewDetails.index                       | mediaReporting.advertisingDetails.podPosition | Dimension | Ad In Pod Position |     |
| Ad Length        | advertising.adAssetReference._xmpDM.duration                 | mediaReporting.advertisingDetails.length      | Metric    | Ad Length      |           |
| Ad Player Name   | advertising.adAssetViewDetails.playerName                    | mediaReporting.advertisingDetails.playerName  | Dimension | Ad Player Name |           |
| Ad Break ID      | advertising.adAssetViewDetails.adBreak._id                   | mediaReporting.advertisingPodDetails.ID       | Dimension | Ad Break ID    |           |
| Ad Name          | advertising.adAssetReference._dc.title                       | mediaReporting.advertisingDetails.friendlyName| Dimension | Ad Name        |           |
| Advertiser       | advertising.adAssetReference.advertiser                      | mediaReporting.advertisingDetails.advertiser  | Dimension | Advertiser     |           |
| Campaign ID      | advertising.adAssetReference.campaign                        | mediaReporting.advertisingDetails.campaignID  | Dimension | Campaign ID    |           |
| Ad Start         | advertising.impressions.value                                | mediaReporting.advertisingDetails.isStarted   | Metric    | Ad Start       |           |
| Ad Complete      | advertising.completes.value                                  | mediaReporting.advertisingDetails.isCompleted | Metric    | Ad Complete    |           |
| Ad Time Spent    | advertising.timePlayed.value                                 | mediaReporting.advertisingDetails.timePlayed  | Metric    | Ad Time Spent  |           |

{style="table-layout:auto"}

## Quality parameters

| Field name             | Current XDM Field Path (Deprecated)                          | Reporting XDM Field Path                      | Data Type | Derived Fields | Notes     |
|------------------------|--------------------------------------------------------------|------------------------------------------------|-----------|----------------|-----------|
| Average Bitrate        | media.mediaTimed.primaryAssetViewDetails.qoe.bitrateAverage.value | mediaReporting.qoeDataDetails.bitrateAverage | Both      | Average Bitrate|           |
| Time To Start          | media.mediaTimed.primaryAssetViewDetails.qoe.timeToStart.value     | mediaReporting.qoeDataDetails.timeToStart     | Both      | Time To Start  |           |
| Dropped Frames         | media.mediaTimed.primaryAssetViewDetails.qoe.droppedFrames.value   | mediaReporting.qoeDataDetails.droppedFrames   | Both      | Dropped Frames |           |
| Buffer Events          | media.mediaTimed.primaryAssetViewDetails.qoe.buffers.value         | mediaReporting.qoeDataDetails.bufferCount     | Both      | Buffer Events  |           |
| Total Buffer Duration  | media.mediaTimed.primaryAssetViewDetails.qoe.bufferTime.value       | mediaReporting.qoeDataDetails.bufferTime      | Both      | Total Buffer Duration |     |
| Bitrate Changes        | media.mediaTimed.primaryAssetViewDetails.qoe.bitrateChanges.value   | mediaReporting.qoeDataDetails.bitrateChangeCount | Both  | Bitrate Changes |         |
| Errors / Error Events  | media.mediaTimed.primaryAssetViewDetails.qoe.errors.value           | mediaReporting.qoeDataDetails.errorCount      | Both      | Errors / Error Events |  |
| Player SDK Error IDs   | media.mediaTimed.primaryAssetViewDetails.qoe.playerSdkErrors        | mediaReporting.qoeDataDetails.playerSdkErrors | Dimension | not supported   | use mediaReporting field |
| External Error IDs     | media.mediaTimed.primaryAssetViewDetails.qoe.externalSdkErrors      | mediaReporting.qoeDataDetails.externalErrors  | Dimension | not supported   | use mediaReporting field |
| Drops Before Start     | media.mediaTimed.dropBeforeStarts.value                            | mediaReporting.qoeDataDetails.isDroppedBeforeStart | Metric | Drops Before Start |     |
| Buffer Impacted Streams| Not supported                                                      | mediaReporting.qoeDataDetails.hasBufferImpactedStreams | Metric | Buffer Impacted Streams | calculated from other events |
| Bitrate Change Impacted Streams | Not supported                                             | mediaReporting.qoeDataDetails.hasBitrateChangeImpactedStreams | Metric | Bitrate Change Impacted Streams | calculated from other events |
| Error Impacted Streams | Not supported                                                      | mediaReporting.qoeDataDetails.hasErrorImpactedStreams | Metric | Error Impacted Streams | calculated from other events |
| Dropped Frame Impacted Streams | Not supported                                              | mediaReporting.qoeDataDetails.hasDroppedFrameImpactedStreams | Metric | Dropped Frame Impacted Streams | calculated from other events |

{style="table-layout:auto"}

## Media Analytics classifications

Media Analytics classifications are ingested into AEP via a separate flow known as ACDC. Each classification group listed in the table below corresponds to a unique dataset within AEP. In CJA, it is necessary to establish a connection between the Media Analytics event dataset and each of the classification datasets.

### Connecting datasets in Customer Journey Analytics

To set up the connection in Customer Journey Analytics:

- Navigate to the **Connections** tab and select **Create new connection**.
- In the Connections interface, choose **Add datasets** and locate the Media Analytics event dataset (used for importing media data via ADC), along with the four relevant classification datasets.

### Configuration details

For each lookup dataset (classification dataset), configure as follows:

- **video dataset**:  
  - Key: `_sandbox.key`  
  - Matching key: `Asset ID (media.mediaTimed.primaryAssetReference._id)`  
  - Data source type: `Web Data`

- **videoad dataset**:  
  - Key: `_sandbox.key`  
  - Matching key: `Ad ID (advertising.adAssetReference._id)`  
  - Data source type: `Web Data`

- **videoadpod dataset**:  
  - Key: `_sandbox.key`  
  - Matching key: `Ad Pod ID (advertising.adAssetViewDetails.adBreak._id)`  
  - Data source type: `Web Data`

- **videochapter dataset**:  
  - Key: `_sandbox.key`  
  - Matching key: `Chapter identity (media.mediaTimed.mediaChapter.chapterAssetReference._id)`  
  - Data source type: `Web Data`

### Reporting considerations

When working with the classification datasets during reporting, ensure that you reference the classification-specific field paths (`ACDC XDM Path`) instead of the standard Media Analytics XDM fields.

## Classifications Table

| Classification name (group) | Field name         | ACDC XDM Path              |
|-----------------------------|--------------------|----------------------------|
| video                       | Key / Asset ID     | `<_sandbox>.key`           |
| video                       | Video Length       | `<_sandbox>.video_length`  |
| video                       | Video Name         | `<_sandbox>.video_name`    |
| video                       | Asset ID           | `<_sandbox>.asset_id`      |
| video                       | First Air Date     | `<_sandbox>.first_air_date`|
| video                       | First Digital Date | `<_sandbox>.first_digital_date`|
| video                       | Content Rating     | `<_sandbox>.content_rating`|
| video                       | Originator         | `<_sandbox>.originator`    |
| videoad                     | Key / Ad ID        | `<_sandbox>.key`           |
| videoad                     | Ad Length          | `<_sandbox>.ad_length`     |
| videoad                     | Ad Name            | `<_sandbox>.ad_name`       |
| videoad                     | Creative ID        | `<_sandbox>.creative_id`   |
| videoadpod                  | Key / Ad Pod ID    | `<_sandbox>.key`           |
| videoadpod                  | Pod Position       | `<_sandbox>.pod_position`  |
| videoadpod                  | Pod Name           | `<_sandbox>.pod_name`      |
| videochapter                | Key / Chapter      | `<_sandbox>.key`           |
| videochapter                | Chapter Length     | `<_sandbox>.chapter_length`|
| videochapter                | Chapter Offset     | `<_sandbox>.chapter_offset`|
| videochapter                | Chapter Position   | `<_sandbox>.chapter_position`|
| videochapter                | Chapter Name       | `<_sandbox>.chapter_name`  |

{style="table-layout:auto"}

## Media Analytics custom variables

In Adobe Analytics, custom variables are assigned to different events or eVars depending on the implementation rules defined within each report suite. As a result, when these custom variables are imported into Adobe Experience Platform (AEP), they are mapped to different XDM paths.

- Events are stored under the path:  
  `_experience.analytics.event<x>to<y>.event<number>.value`

- eVars are stored under the path:  
  `_experience.analytics.customDimensions.eVars.eVar<number>`

In both cases, the `<number>` corresponds to the specific event or eVar number used in the original Adobe Analytics report suite configuration.

### Custom variables

| Field name              | XDM Path                                                                 | Data Type |
|-------------------------|--------------------------------------------------------------------------|-----------|
| Media Downloaded Flag   | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |
| SDK Version             | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| VHL Version             | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| Stream Format           | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| First Air Date          | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| First Digital Date      | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| Federated Data          | _experience.analytics.customDimensions.eVars.eVar<number> and _experience.analytics.event<x>to<y>.event<number>.value | Both      |
| Estimated Streams       | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |
| Ad Count                | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |
| Chapter Count           | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |
| Creative ID             | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| Site ID                 | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| Creative URL            | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| Placement ID            | _experience.analytics.customDimensions.eVars.eVar<number>               | Dimension |
| Frames per Second       | _experience.analytics.customDimensions.eVars.eVar<number> and _experience.analytics.event<x>to<y>.event<number>.value | Both      |
| Media SDK Error IDs     | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |
| Stalling Impacted Streams | _experience.analytics.event<x>to<y>.event<number>.value               | Metric    |
| Stalling Events         | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |
| Total Stalling Duration | _experience.analytics.event<x>to<y>.event<number>.value                 | Metric    |

---

**End of Media Analytics Paths Documentation**






