---
title: Media Analytics parameters mapping for Adobe Experience Platform and Customer Journey Analytics
description: XDM field path mapping for Media Analytics parameters used with the Analytics Source Connector and Customer Journey Analytics.
feature: Streaming Media
role: User, Admin, Developer
exl-id: 79203a2f-8158-44f2-83b2-146179be9180
TQID: https://experienceleague.adobe.com/ct8mDbIpg15Jzvf1MRaG4XFtuxbq-EUKPe106zyO7zQ
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
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
---
# Media Analytics parameters mapping for Adobe Experience Platform and Customer Journey Analytics

This document provides a comprehensive list of all Media Analytics parameters utilized within Adobe Experience Platform and Customer Journey Analytics. It is intended to support the integration of data imported from Adobe Analytics to Platform via the [Analytics Source Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/analytics) or the [Analytics Source Connector for Classifications](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/classifications), mapping each parameter to its corresponding XDM field path.

>[!NOTE]
>
>This reference applies to organizations using the [Analytics source connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/analytics) to bring streaming media data from Adobe Analytics into Adobe Experience Platform for use with Customer Journey Analytics reporting or other Platform services. These changes do not impact Adobe Analytics as a standalone application, including data collection, processing, and reporting.

## Media Analytics reserved variables

As of October 2025, the `media.mediaTimed` XDM field path is fully deprecated and replaced by `mediaReporting`. Data ingested after October 2025 includes only `mediaReporting` fields. Earlier data remains available under the legacy field path, reflected in the tables below under **Legacy XDM field**.

### Keep-alive call behavior

With the Analytics source connector for streaming media, keep-alive calls from Adobe Analytics are now ingested into Adobe Experience Platform. This may affect Customer Journey Analytics reporting:

* **Session counts**: Keep-alive calls help maintain active user sessions even without direct media interactions. These calls are generated every 20 minutes after the last event per media playback. To ensure optimal session tracking, configure visit expiration to 30 minutes in the data view.

* **Event counts**: Keep-alive calls now count toward the Customer Journey Analytics Events metric. To exclude them, create a filter that excludes events with Event Type `media.keepalive`.

## Streaming Media parameters

| Field name | Legacy XDM field | Reporting XDM Field Path | Data Type | Derived field | Notes |
| --- | --- | --- | --- | --- | --- |
| [[!UICONTROL Stream Type]](/help/reporting/dimensions/stream-type.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference.streamType` | `xdm.mediaReporting.`<br>`sessionDetails.streamType` | Dimension | [[!UICONTROL Stream Type]](/help/reporting/dimensions/stream-type.md) | |
| [[!UICONTROL Content ID]](/help/reporting/dimensions/asset-id.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._id` | `xdm.mediaReporting.`<br>`sessionDetails.name` | Dimension | [[!UICONTROL Content ID]](/help/reporting/dimensions/asset-id.md) | |
| [[!UICONTROL Content Length]](/help/reporting/dimensions/content-length.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._xmpDM.duration` | `xdm.mediaReporting.`<br>`sessionDetails.length` | Dimension | [[!UICONTROL Content Length]](/help/reporting/dimensions/content-length.md) | |
| [[!UICONTROL Content Type]](/help/reporting/dimensions/content-type.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.broadcastContentType` | `xdm.mediaReporting.`<br>`sessionDetails.contentType` | Dimension | [[!UICONTROL Content Type]](/help/reporting/dimensions/content-type.md) | |
| [[!UICONTROL Media Session ID]](/help/reporting/dimensions/media-session-id.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails._id` | `xdm.mediaReporting.`<br>`sessionDetails.ID` | Dimension | [[!UICONTROL Media Session ID]](/help/reporting/dimensions/media-session-id.md) | |
| [[!UICONTROL Content Player Name]](/help/reporting/dimensions/content-player-name.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.playerName` | `xdm.mediaReporting.`<br>`sessionDetails.playerName` | Dimension | [[!UICONTROL Content Player Name]](/help/reporting/dimensions/content-player-name.md) | |
| [[!UICONTROL Content Channel]](/help/reporting/dimensions/content-channel.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.broadcastChannel` | `xdm.mediaReporting.`<br>`sessionDetails.channel` | Dimension | [[!UICONTROL Content Channel]](/help/reporting/dimensions/content-channel.md) | |
| [[!UICONTROL Content Segment]](/help/reporting/dimensions/content-segment.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.videoSegment` | `xdm.mediaReporting.`<br>`sessionDetails.segment` | Dimension | [[!UICONTROL Content Segment]](/help/reporting/dimensions/content-segment.md) | |
| [[!UICONTROL Content Name]](/help/reporting/dimensions/content-name.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._dc.title` | `xdm.mediaReporting.`<br>`sessionDetails.friendlyName` | Dimension | [[!UICONTROL Content Name]](/help/reporting/dimensions/content-name.md) | |
| Video Path | *Not used in AEP/CJA* | | | | Adobe Analytics specific property |
| [[!UICONTROL Show]](/help/reporting/dimensions/show.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._iptc4xmpExt.Series._iptc4xmpExt.Name` | `xdm.mediaReporting.`<br>`sessionDetails.show` | Dimension | [[!UICONTROL Show]](/help/reporting/dimensions/show.md) | |
| [[!UICONTROL Season]](/help/reporting/dimensions/season.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._iptc4xmpExt.Season._iptc4xmpExt.Name` | `xdm.mediaReporting.`<br>`sessionDetails.season` | Dimension | [[!UICONTROL Season]](/help/reporting/dimensions/season.md) | |
| [[!UICONTROL Episode]](/help/reporting/dimensions/episode.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._iptc4xmpExt.Episode._iptc4xmpExt.Name` | `xdm.mediaReporting.`<br>`sessionDetails.episode` | Dimension | [[!UICONTROL Episode]](/help/reporting/dimensions/episode.md) | |
| [[!UICONTROL Genre]](/help/reporting/dimensions/genre.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._iptc4xmpExt.Genre` | `xdm.mediaReporting.`<br>`sessionDetails.genreList` | Dimension | not supported | Use `mediaReporting` field |
| [[!UICONTROL Network]](/help/reporting/dimensions/network.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.broadcastNetwork` | `xdm.mediaReporting.`<br>`sessionDetails.network` | Dimension | [[!UICONTROL Network]](/help/reporting/dimensions/network.md) | |
| [[!UICONTROL Show Type]](/help/reporting/dimensions/show-type.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference.showType` | `xdm.mediaReporting.`<br>`sessionDetails.showType` | Dimension | [[!UICONTROL Show Type]](/help/reporting/dimensions/show-type.md) | |
| [[!UICONTROL MVPD]](/help/reporting/dimensions/mvpd.md) | `xdm.media.mediaTimed.`<br>`idp` | `xdm.mediaReporting.`<br>`sessionDetails.mvpd` | Dimension | [[!UICONTROL MVPD]](/help/reporting/dimensions/mvpd.md) | |
| [[!UICONTROL Authorized]](/help/reporting/metrics/authorized.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.authorized` | Dimension | [[!UICONTROL Authorized]](/help/reporting/metrics/authorized.md) | |
| [[!UICONTROL Day Part]](/help/reporting/dimensions/day-part.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.dayPart` | Dimension | [[!UICONTROL Day Part]](/help/reporting/dimensions/day-part.md) | |
| [[!UICONTROL Media Feed Type]](/help/reporting/dimensions/media-feed-type.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.sourceFeed` | `xdm.mediaReporting.`<br>`sessionDetails.feed` | Dimension | [[!UICONTROL Media Feed Type]](/help/reporting/dimensions/media-feed-type.md) | |
| [[!UICONTROL Artist]](/help/reporting/dimensions/artist.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._xmpDM.artist` | `xdm.mediaReporting.`<br>`sessionDetails.artist` | Dimension | [[!UICONTROL Artist]](/help/reporting/dimensions/artist.md) | |
| [[!UICONTROL Album]](/help/reporting/dimensions/album.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._xmpDM.album` | `xdm.mediaReporting.`<br>`sessionDetails.album` | Dimension | [[!UICONTROL Album]](/help/reporting/dimensions/album.md) | |
| [[!UICONTROL Label]](/help/reporting/dimensions/label.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.label` | Dimension | [[!UICONTROL Label]](/help/reporting/dimensions/label.md) | |
| [[!UICONTROL Author]](/help/reporting/dimensions/author.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.author` | Dimension | [[!UICONTROL Author]](/help/reporting/dimensions/author.md) | |
| [[!UICONTROL Station]](/help/reporting/dimensions/station.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._id3.Audio._id3.TRSN` | `xdm.mediaReporting.`<br>`sessionDetails.station` | Dimension | [[!UICONTROL Station]](/help/reporting/dimensions/station.md) | |
| [[!UICONTROL Publisher]](/help/reporting/dimensions/publisher.md) | `xdm.media.mediaTimed.`<br>`primaryAssetReference._id3.Audio._id3.TPUB` | `xdm.mediaReporting.`<br>`sessionDetails.publisher` | Dimension | [[!UICONTROL Publisher]](/help/reporting/dimensions/publisher.md) | |
| [[!UICONTROL Media Starts]](/help/reporting/metrics/media-starts.md) | `xdm.media.mediaTimed.`<br>`impressions.value` | `xdm.mediaReporting.`<br>`sessionDetails.isViewed` | Metric | [[!UICONTROL Media Starts]](/help/reporting/metrics/media-starts.md) | |
| [[!UICONTROL Content Starts]](/help/reporting/metrics/content-starts.md) | `xdm.media.mediaTimed.`<br>`starts.value` | `xdm.mediaReporting.`<br>`sessionDetails.isPlayed` | Metric | [[!UICONTROL Content Starts]](/help/reporting/metrics/content-starts.md) | |
| [[!UICONTROL Content Complete]](/help/reporting/metrics/content-completes.md) | `xdm.media.mediaTimed.`<br>`completes.value` | `xdm.mediaReporting.`<br>`sessionDetails.isCompleted` | Metric | [[!UICONTROL Content Complete]](/help/reporting/metrics/content-completes.md) | |
| [[!UICONTROL Content Time Spent]](/help/reporting/metrics/content-time-spent.md) | `xdm.media.mediaTimed.`<br>`timePlayed.value` | `xdm.mediaReporting.`<br>`sessionDetails.timePlayed` | Metric | [[!UICONTROL Content Time Spent]](/help/reporting/metrics/content-time-spent.md) | |
| [[!UICONTROL Media Time Spent]](/help/reporting/metrics/media-time-spent.md) | `xdm.media.mediaTimed.`<br>`totalTimePlayed.value` | `xdm.mediaReporting.`<br>`sessionDetails.totalTimePlayed` | Metric | [[!UICONTROL Media Time Spent]](/help/reporting/metrics/media-time-spent.md) | |
| [[!UICONTROL Unique Time Played]](/help/reporting/metrics/unique-time-played.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.uniqueTimePlayed` | Metric | [[!UICONTROL Unique Time Played]](/help/reporting/metrics/unique-time-played.md) | |
| [[!UICONTROL 10% Progress Marker]](/help/reporting/metrics/progress-markers.md) | `xdm.media.mediaTimed.`<br>`progress10.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasProgress10` | Metric | [[!UICONTROL 10% Progress Marker]](/help/reporting/metrics/progress-markers.md) | |
| [[!UICONTROL 25% Progress Marker]](/help/reporting/metrics/progress-markers.md) | `xdm.media.mediaTimed.`<br>`progress25.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasProgress25` | Metric | [[!UICONTROL 25% Progress Marker]](/help/reporting/metrics/progress-markers.md) | |
| [[!UICONTROL 50% Progress Marker]](/help/reporting/metrics/progress-markers.md) | `xdm.media.mediaTimed.`<br>`progress50.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasProgress50` | Metric | [[!UICONTROL 50% Progress Marker]](/help/reporting/metrics/progress-markers.md) | |
| [[!UICONTROL 75% Progress Marker]](/help/reporting/metrics/progress-markers.md) | `xdm.media.mediaTimed.`<br>`progress75.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasProgress75` | Metric | [[!UICONTROL 75% Progress Marker]](/help/reporting/metrics/progress-markers.md) | |
| [[!UICONTROL 95% Progress Marker]](/help/reporting/metrics/progress-markers.md) | `xdm.media.mediaTimed.`<br>`progress95.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasProgress95` | Metric | [[!UICONTROL 95% Progress Marker]](/help/reporting/metrics/progress-markers.md) | |
| [[!UICONTROL Average Minute Audience]](/help/reporting/metrics/average-minute-audience.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.averageMinuteAudience` | Metric | [[!UICONTROL Average Minute Audience]](/help/reporting/metrics/average-minute-audience.md) | |
| Seconds Since Last Call | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.sessionTimeout` | `xdm.mediaReporting.`<br>`sessionDetails.secondsSinceLastCall` | Metric | Seconds Since Last Call | |
| [[!UICONTROL Paused Impacted Streams]](/help/reporting/metrics/paused-impacted-streams.md) | Not supported | `xdm.mediaReporting.`<br>`sessionDetails.hasPauseImpactedStreams` | Metric | [[!UICONTROL Paused Impacted Streams]](/help/reporting/metrics/paused-impacted-streams.md) | we cover mediaTimed by calculating this value from other events |
| [[!UICONTROL Pause Events]](/help/reporting/metrics/pause-events.md) | `xdm.media.mediaTimed.`<br>`pauses.value` | `xdm.mediaReporting.`<br>`sessionDetails.pauseCount` | Metric | [[!UICONTROL Pause Events]](/help/reporting/metrics/pause-events.md) | |
| [[!UICONTROL Total Pause Duration]](/help/reporting/metrics/total-pause-duration.md) | `xdm.media.mediaTimed.`<br>`pauseTime.value` | `xdm.mediaReporting.`<br>`sessionDetails.pauseTime` | Metric | [[!UICONTROL Total Pause Duration]](/help/reporting/metrics/total-pause-duration.md) | |
| [[!UICONTROL Content Resumes]](/help/reporting/metrics/content-resumes.md) | `xdm.media.mediaTimed.`<br>`resumes.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasResume` | Metric | [[!UICONTROL Content Resumes]](/help/reporting/metrics/content-resumes.md) | |
| [[!UICONTROL Content Segment Views]](/help/reporting/metrics/content-segment-views.md) | `xdm.media.mediaTimed.`<br>`mediaSegmentViews.value` | `xdm.mediaReporting.`<br>`sessionDetails.hasSegmentView` | Metric | [[!UICONTROL Content Segment Views]](/help/reporting/metrics/content-segment-views.md) | |

## Player state parameters update

| Field name | Legacy XDM field | Reporting XDM Field Path | Data Type | Derived field | Notes |
| --- | --- | --- | --- | --- | --- |
| Streams Impacted by Player States | Not supported | `xdm.mediaReporting.`<br>`states.isSet` | Metric | not supported | use `mediaReporting` field |
| Player States Counts | Not supported | `xdm.mediaReporting.`<br>`states.count` | Metric | not supported | use `mediaReporting` field |
| Player States Total Duration | Not supported | `xdm.mediaReporting.`<br>`states.time` | Metric | not supported | use `mediaReporting` field |
| Player State Name | Not supported | `xdm.mediaReporting.`<br>`states.name` | Dimension | not supported | use `mediaReporting` field |

## Chapter parameters

| Field name | Legacy XDM field | Reporting XDM Field Path | Data Type | Derived field | Notes |
| --- | --- | --- | --- | --- | --- |
| [[!UICONTROL Chapter]](/help/reporting/dimensions/chapter.md) | `xdm.media.mediaTimed.`<br>`mediaChapter.chapterAssetReference._id` | `xdm.mediaReporting.`<br>`chapterDetails.ID` | Dimension | [[!UICONTROL Chapter]](/help/reporting/dimensions/chapter.md) | |
| [[!UICONTROL Chapter Start]](/help/reporting/metrics/chapter-starts.md) | `xdm.media.mediaTimed.`<br>`mediaChapter.impressions.value` | `xdm.mediaReporting.`<br>`chapterDetails.isStarted` | Metric | [[!UICONTROL Chapter Start]](/help/reporting/metrics/chapter-starts.md) | |
| [[!UICONTROL Chapter Complete]](/help/reporting/metrics/chapter-completes.md) | `xdm.media.mediaTimed.`<br>`mediaChapter.completes.value` | `xdm.mediaReporting.`<br>`chapterDetails.isCompleted` | Metric | [[!UICONTROL Chapter Complete]](/help/reporting/metrics/chapter-completes.md) | |
| [[!UICONTROL Chapter Time Spent]](/help/reporting/metrics/chapter-time-spent.md) | `xdm.media.mediaTimed.`<br>`mediaChapter.timePlayed.value` | `xdm.mediaReporting.`<br>`chapterDetails.timePlayed` | Metric | [[!UICONTROL Chapter Time Spent]](/help/reporting/metrics/chapter-time-spent.md) | |

## Ad parameters

| Field name | Legacy XDM field | Reporting XDM Field Path | Data Type | Derived field | Notes |
| --- | --- | --- | --- | --- | --- |
| [[!UICONTROL Ad ID]](/help/reporting/dimensions/ad.md) | `xdm.advertising.`<br>`adAssetReference._id` | `xdm.mediaReporting.`<br>`advertisingDetails.name` | Dimension | [[!UICONTROL Ad ID]](/help/reporting/dimensions/ad.md) | |
| [[!UICONTROL Ad In Pod Position]](/help/reporting/dimensions/ad-in-pod-position.md) | `xdm.advertising.`<br>`adAssetViewDetails.index` | `xdm.mediaReporting.`<br>`advertisingDetails.podPosition` | Dimension | [[!UICONTROL Ad In Pod Position]](/help/reporting/dimensions/ad-in-pod-position.md) | |
| [[!UICONTROL Ad Length]](/help/reporting/dimensions/ad-length.md) | `xdm.advertising.`<br>`adAssetReference._xmpDM.duration` | `xdm.mediaReporting.`<br>`advertisingDetails.length` | Metric | [[!UICONTROL Ad Length]](/help/reporting/dimensions/ad-length.md) | |
| [[!UICONTROL Ad Player Name]](/help/reporting/dimensions/ad-player-name.md) | `xdm.advertising.`<br>`adAssetViewDetails.playerName` | `xdm.mediaReporting.`<br>`advertisingDetails.playerName` | Dimension | [[!UICONTROL Ad Player Name]](/help/reporting/dimensions/ad-player-name.md) | |
| [[!UICONTROL Ad Break ID]](/help/reporting/dimensions/ad-pod.md) | `xdm.advertising.`<br>`adAssetViewDetails.adBreak._id` | `xdm.mediaReporting.`<br>`advertisingPodDetails.ID` | Dimension | [[!UICONTROL Ad Break ID]](/help/reporting/dimensions/ad-pod.md) | |
| [[!UICONTROL Ad Name]](/help/reporting/dimensions/ad-name.md) | `xdm.advertising.`<br>`adAssetReference._dc.title` | `xdm.mediaReporting.`<br>`advertisingDetails.friendlyName` | Dimension | [[!UICONTROL Ad Name]](/help/reporting/dimensions/ad-name.md) | |
| [[!UICONTROL Advertiser]](/help/reporting/dimensions/advertiser.md) | `xdm.advertising.`<br>`adAssetReference.advertiser` | `xdm.mediaReporting.`<br>`advertisingDetails.advertiser` | Dimension | [[!UICONTROL Advertiser]](/help/reporting/dimensions/advertiser.md) | |
| [[!UICONTROL Campaign ID]](/help/reporting/dimensions/campaign-id.md) | `xdm.advertising.`<br>`adAssetReference.campaign` | `xdm.mediaReporting.`<br>`advertisingDetails.campaignID` | Dimension | [[!UICONTROL Campaign ID]](/help/reporting/dimensions/campaign-id.md) | |
| [[!UICONTROL Ad Start]](/help/reporting/metrics/ad-starts.md) | `xdm.advertising.`<br>`impressions.value` | `xdm.mediaReporting.`<br>`advertisingDetails.isStarted` | Metric | [[!UICONTROL Ad Start]](/help/reporting/metrics/ad-starts.md) | |
| [[!UICONTROL Ad Complete]](/help/reporting/metrics/ad-completes.md) | `xdm.advertising.`<br>`completes.value` | `xdm.mediaReporting.`<br>`advertisingDetails.isCompleted` | Metric | [[!UICONTROL Ad Complete]](/help/reporting/metrics/ad-completes.md) | |
| [[!UICONTROL Ad Time Spent]](/help/reporting/metrics/ad-time-spent.md) | `xdm.advertising.`<br>`timePlayed.value` | `xdm.mediaReporting.`<br>`advertisingDetails.timePlayed` | Metric | [[!UICONTROL Ad Time Spent]](/help/reporting/metrics/ad-time-spent.md) | |

## Quality parameters

| Field name | Legacy XDM field | Reporting XDM Field Path | Data Type | Derived Fields | Notes |
| --- | --- | --- | --- | --- | --- |
| [[!UICONTROL Average Bitrate]](/help/reporting/metrics/average-bitrate.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.bitrateAverage.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.bitrateAverage` | Both | [[!UICONTROL Average Bitrate]](/help/reporting/metrics/average-bitrate.md) | |
| [[!UICONTROL Time To Start]](/help/reporting/metrics/time-to-start.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.timeToStart.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.timeToStart` | Both | [[!UICONTROL Time To Start]](/help/reporting/metrics/time-to-start.md) | |
| [[!UICONTROL Dropped Frames]](/help/reporting/metrics/dropped-frames.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.droppedFrames.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.droppedFrames` | Both | [[!UICONTROL Dropped Frames]](/help/reporting/metrics/dropped-frames.md) | |
| [[!UICONTROL Buffer Events]](/help/reporting/metrics/buffer-events.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.buffers.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.bufferCount` | Both | [[!UICONTROL Buffer Events]](/help/reporting/metrics/buffer-events.md) | |
| [[!UICONTROL Total Buffer Duration]](/help/reporting/metrics/total-buffer-duration.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.bufferTime.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.bufferTime` | Both | [[!UICONTROL Total Buffer Duration]](/help/reporting/metrics/total-buffer-duration.md) | |
| [[!UICONTROL Bitrate Changes]](/help/reporting/metrics/bitrate-changes.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.bitrateChanges.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.bitrateChangeCount` | Both | [[!UICONTROL Bitrate Changes]](/help/reporting/metrics/bitrate-changes.md) | |
| [[!UICONTROL Errors / Error Events]](/help/reporting/metrics/error-events.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.errors.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.errorCount` | Both | [[!UICONTROL Errors / Error Events]](/help/reporting/metrics/error-events.md) | |
| [[!UICONTROL Player SDK Error IDs]](/help/reporting/dimensions/player-sdk-error-ids.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.playerSdkErrors` | `xdm.mediaReporting.`<br>`qoeDataDetails.playerSdkErrors` | Dimension | not supported | use `mediaReporting` field |
| [[!UICONTROL External Error IDs]](/help/reporting/dimensions/external-error-ids.md) | `xdm.media.mediaTimed.`<br>`primaryAssetViewDetails.qoe.externalSdkErrors` | `xdm.mediaReporting.`<br>`qoeDataDetails.externalErrors` | Dimension | not supported | use `mediaReporting` field |
| [[!UICONTROL Drops Before Start]](/help/reporting/metrics/drops-before-start.md) | `xdm.media.mediaTimed.`<br>`dropBeforeStarts.value` | `xdm.mediaReporting.`<br>`qoeDataDetails.isDroppedBeforeStart` | Metric | [[!UICONTROL Drops Before Start]](/help/reporting/metrics/drops-before-start.md) | |
| [[!UICONTROL Buffer Impacted Streams]](/help/reporting/metrics/buffer-impacted-streams.md) | Not supported | `xdm.mediaReporting.`<br>`qoeDataDetails.hasBufferImpactedStreams` | Metric | [[!UICONTROL Buffer Impacted Streams]](/help/reporting/metrics/buffer-impacted-streams.md) | calculated from other events |
| [[!UICONTROL Bitrate Change Impacted Streams]](/help/reporting/metrics/bitrate-change-impacted-streams.md) | Not supported | `xdm.mediaReporting.`<br>`qoeDataDetails.hasBitrateChangeImpactedStreams` | Metric | [[!UICONTROL Bitrate Change Impacted Streams]](/help/reporting/metrics/bitrate-change-impacted-streams.md) | calculated from other events |
| [[!UICONTROL Error Impacted Streams]](/help/reporting/metrics/error-impacted-streams.md) | Not supported | `xdm.mediaReporting.`<br>`qoeDataDetails.hasErrorImpactedStreams` | Metric | [[!UICONTROL Error Impacted Streams]](/help/reporting/metrics/error-impacted-streams.md) | calculated from other events |
| [[!UICONTROL Dropped Frame Impacted Streams]](/help/reporting/metrics/dropped-frame-impacted-streams.md) | Not supported | `xdm.mediaReporting.`<br>`qoeDataDetails.hasDroppedFrameImpactedStreams` | Metric | [[!UICONTROL Dropped Frame Impacted Streams]](/help/reporting/metrics/dropped-frame-impacted-streams.md) | calculated from other events |

## Media Analytics classifications

Media Analytics classifications are ingested into AEP via a separate flow known as ACDC. Each classification group listed in the table below corresponds to a unique dataset within AEP. In CJA, it is necessary to establish a connection between the Media Analytics event dataset and each of the classification datasets.

### Connecting datasets in Customer Journey Analytics

To set up the connection in Customer Journey Analytics:

* Navigate to the **Connections** tab and select **Create new connection**.
* In the Connections interface, choose **Add datasets** and locate the Media Analytics event dataset (used for importing media data via ADC), along with the four relevant classification datasets.

### Configuration details

For each lookup dataset (classification dataset), configure as follows:

* **video dataset**:  
  * Key: `_sandbox.key`  
  * Matching key: `Asset ID (media.mediaTimed.primaryAssetReference._id)`  
  * Data source type: `Web Data`

* **videoad dataset**:  
  * Key: `_sandbox.key`  
  * Matching key: `Ad ID (advertising.adAssetReference._id)`  
  * Data source type: `Web Data`

* **videoadpod dataset**:  
  * Key: `_sandbox.key`  
  * Matching key: `Ad Pod ID (advertising.adAssetViewDetails.adBreak._id)`  
  * Data source type: `Web Data`

* **videochapter dataset**:  
  * Key: `_sandbox.key`  
  * Matching key: `Chapter identity (media.mediaTimed.mediaChapter.chapterAssetReference._id)`  
  * Data source type: `Web Data`

### Reporting considerations

When working with the classification datasets during reporting, ensure that you reference the classification-specific field paths (`ACDC XDM Path`) instead of the standard Media Analytics XDM fields.

## Classifications Table

| Classification name (group) | Field name | ACDC XDM Path |
| --- | --- | --- |
| video | Key / Asset ID | `xdm.<_sandbox>.key` |
| video | Video Length | `xdm.<_sandbox>.video_length` |
| video | Video Name | `xdm.<_sandbox>.video_name` |
| video | [[!UICONTROL Asset ID]](/help/reporting/dimensions/asset-id.md) | `xdm.<_sandbox>.asset_id` |
| video | [[!UICONTROL First Air Date]](/help/reporting/dimensions/first-air-date.md) | `xdm.<_sandbox>.first_air_date` |
| video | [[!UICONTROL First Digital Date]](/help/reporting/dimensions/first-digital-date.md) | `xdm.<_sandbox>.first_digital_date` |
| video | [[!UICONTROL Content Rating]](/help/reporting/dimensions/content-rating.md) | `xdm.<_sandbox>.content_rating` |
| video | [[!UICONTROL Originator]](/help/reporting/dimensions/originator.md) | `xdm.<_sandbox>.originator` |
| videoad | Key / Ad ID | `xdm.<_sandbox>.key` |
| videoad | [[!UICONTROL Ad Length]](/help/reporting/dimensions/ad-length.md) | `xdm.<_sandbox>.ad_length` |
| videoad | [[!UICONTROL Ad Name]](/help/reporting/dimensions/ad-name.md) | `xdm.<_sandbox>.ad_name` |
| videoad | [[!UICONTROL Creative ID]](/help/reporting/dimensions/creative-id.md) | `xdm.<_sandbox>.creative_id` |
| videoadpod | Key / Ad Pod ID | `xdm.<_sandbox>.key` |
| videoadpod | [[!UICONTROL Pod Position]](/help/reporting/dimensions/pod-position.md) | `xdm.<_sandbox>.pod_position` |
| videoadpod | [[!UICONTROL Pod Name]](/help/reporting/dimensions/pod-name.md) | `xdm.<_sandbox>.pod_name` |
| videochapter | Key / Chapter | `xdm.<_sandbox>.key` |
| videochapter | [[!UICONTROL Chapter Length]](/help/reporting/dimensions/chapter-length.md) | `xdm.<_sandbox>.chapter_length` |
| videochapter | [[!UICONTROL Chapter Offset]](/help/reporting/dimensions/chapter-offset.md) | `xdm.<_sandbox>.chapter_offset` |
| videochapter | [[!UICONTROL Chapter Position]](/help/reporting/dimensions/chapter-position.md) | `xdm.<_sandbox>.chapter_position` |
| videochapter | [[!UICONTROL Chapter Name]](/help/reporting/dimensions/chapter-name.md) | `xdm.<_sandbox>.chapter_name` |

## Media Analytics custom variables

In Adobe Analytics, custom variables are assigned to different events or eVars depending on the implementation rules defined within each report suite. As a result, when these custom variables are imported into Adobe Experience Platform (AEP), they are mapped to different XDM paths.

* Events are stored under the path: 

  `_experience.analytics.event<x>to<y>.event<number>.value`

* eVars are stored under the path:

  `_experience.analytics.customDimensions.eVars.eVar<number>`

In both cases, the `<number>` corresponds to the specific event or eVar number used in the original Adobe Analytics report suite configuration.

### Custom variables

| Field name | XDM Path | Data Type |
| --- | --- | --- |
| [[!UICONTROL Media Downloaded Flag]](/help/reporting/dimensions/media-downloaded-flag.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| SDK Version | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| Media Library Version | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL Stream Format]](/help/reporting/dimensions/stream-format.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL First Air Date]](/help/reporting/dimensions/first-air-date.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL First Digital Date]](/help/reporting/dimensions/first-digital-date.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL Federated Data]](/help/reporting/metrics/federated-data.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>`<br>and<br>`xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Both |
| [[!UICONTROL Estimated Streams]](/help/reporting/metrics/estimated-streams.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| [[!UICONTROL Ad Count]](/help/reporting/metrics/ad-count.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| [[!UICONTROL Chapter Count]](/help/reporting/metrics/chapter-count.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| [[!UICONTROL Creative ID]](/help/reporting/dimensions/creative-id.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL Site ID]](/help/reporting/dimensions/site-id.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL Creative URL]](/help/reporting/dimensions/creative-url.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| [[!UICONTROL Placement ID]](/help/reporting/dimensions/placement-id.md) | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>` | Dimension |
| Frames per Second | `xdm._experience.analytics.`<br>`customDimensions.eVars.eVar<number>`<br>and<br>`xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Both |
| Media SDK Error IDs | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| [[!UICONTROL Stalling Impacted Streams]](/help/reporting/metrics/stall-impacted-streams.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| [[!UICONTROL Stalling Events]](/help/reporting/metrics/stall-events.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
| [[!UICONTROL Total Stalling Duration]](/help/reporting/metrics/total-stalling-duration.md) | `xdm._experience.analytics.`<br>`event<x>to<y>.event<number>.value` | Metric |
