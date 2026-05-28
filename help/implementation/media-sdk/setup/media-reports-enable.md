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
# Media reports enablement

Each report suite that collects media metrics must be configured before media data is sent.

1. In [Adobe Analytics](https://experience.adobe.com/analytics), navigate to **[!UICONTROL Admin]** &rarr; **[!UICONTROL Report suites]**.
1. Select the report suite(s) that collect media data. Select **[!UICONTROL Edit Settings]** &rarr; **[!UICONTROL Media Management]** &rarr; **[!UICONTROL Media Reporting]**.

    ![Report suite manager menu screenshot](assets/media-reporting.png)

1. On the **[!UICONTROL Media Reporting]** page, enable the desired streaming media components (see below).

1. Select **[!UICONTROL Save].**

   If this report suite is already configured to collect media data, after you click **[!UICONTROL Save]**, an additional configuration page is displayed. If you see the **[!UICONTROL Media Core measurement]** page, continue to the next step.

## Available streaming media modules

Media measurement includes the following modules:

* **[!UICONTROL Media Core]**: Required for all streaming media tracking. It reserves solution variables for content playback and session data.
  * **Dimensions:**
    * [[!UICONTROL Content]](/help/reporting/dimensions/content.md)
    * [[!UICONTROL Content channel]](/help/reporting/dimensions/content-channel.md)
    * [[!UICONTROL Content length (variable)]](/help/reporting/dimensions/content-length.md)
    * [[!UICONTROL Content name (variable)]](/help/reporting/dimensions/content-name.md)
    * [[!UICONTROL Content player name]](/help/reporting/dimensions/content-player-name.md)
    * [[!UICONTROL Content segment]](/help/reporting/dimensions/content-segment.md)
    * [[!UICONTROL Content type]](/help/reporting/dimensions/content-type.md)
    * [[!UICONTROL Media path]](/help/reporting/dimensions/media-path.md)
    * [[!UICONTROL Media session ID]](/help/reporting/dimensions/media-session-id.md)
    * [[!UICONTROL Stream type]](/help/reporting/dimensions/stream-type.md)
  * **Metrics:**
    * [[!UICONTROL Average minute audience]](/help/reporting/metrics/average-minute-audience.md)
    * [[!UICONTROL Content completes]](/help/reporting/metrics/content-completes.md)
    * [[!UICONTROL Content resumes]](/help/reporting/metrics/content-resumes.md)
    * [[!UICONTROL Content segment views]](/help/reporting/metrics/content-segment-views.md)
    * [[!UICONTROL Content starts]](/help/reporting/metrics/content-starts.md)
    * [[!UICONTROL Content time spent]](/help/reporting/metrics/content-time-spent.md)
    * [[!UICONTROL Media starts]](/help/reporting/metrics/media-starts.md)
    * [[!UICONTROL Pause events]](/help/reporting/metrics/pause-events.md)
    * [[!UICONTROL Paused impacted streams]](/help/reporting/metrics/paused-impacted-streams.md)
    * [[!UICONTROL Progress markers]](/help/reporting/metrics/progress-markers.md)
    * [[!UICONTROL Total pause duration]](/help/reporting/metrics/total-pause-duration.md)
    * [[!UICONTROL Unique time played]](/help/reporting/metrics/unique-time-played.md)
* **[!UICONTROL Media Ads]**: Enables tracking of advertisements within the media content.
  * **Dimensions:**
    * [[!UICONTROL Ad]](/help/reporting/dimensions/ad.md)
    * [[!UICONTROL Ad in pod position]](/help/reporting/dimensions/ad-in-pod-position.md)
    * [[!UICONTROL Ad length (variable)]](/help/reporting/dimensions/ad-length.md)
    * [[!UICONTROL Ad name (variable)]](/help/reporting/dimensions/ad-name.md)
    * [[!UICONTROL Ad player name]](/help/reporting/dimensions/ad-player-name.md)
    * [[!UICONTROL Ad pod]](/help/reporting/dimensions/ad-pod.md)
    * [[!UICONTROL Advertiser]](/help/reporting/dimensions/advertiser.md)
    * [[!UICONTROL Campaign ID]](/help/reporting/dimensions/campaign-id.md)
  * **Classification dimensions:**
    * [[!UICONTROL Asset ID]](/help/reporting/dimensions/asset-id.md)
    * [[!UICONTROL Content rating]](/help/reporting/dimensions/content-rating.md)
    * [[!UICONTROL Creative ID]](/help/reporting/dimensions/creative-id.md)
    * [[!UICONTROL First air date]](/help/reporting/dimensions/first-air-date.md)
    * [[!UICONTROL First digital date]](/help/reporting/dimensions/first-digital-date.md)
    * [[!UICONTROL Pod name]](/help/reporting/dimensions/pod-name.md)
    * [[!UICONTROL Pod position]](/help/reporting/dimensions/pod-position.md)
  * **Metrics:**
    * [[!UICONTROL Ad completes]](/help/reporting/metrics/ad-completes.md)
    * [[!UICONTROL Ad starts]](/help/reporting/metrics/ad-starts.md)
    * [[!UICONTROL Ad time spent]](/help/reporting/metrics/ad-time-spent.md)
    * [[!UICONTROL Media time spent]](/help/reporting/metrics/media-time-spent.md)
* **[!UICONTROL Media Chapters]**: Enables tracking of chapters within media content.
  * **Dimension:**
    * [[!UICONTROL Chapter]](/help/reporting/dimensions/chapter.md)
  * **Classification dimensions:**
    * [[!UICONTROL Chapter length]](/help/reporting/dimensions/chapter-length.md)
    * [[!UICONTROL Chapter name]](/help/reporting/dimensions/chapter-name.md)
    * [[!UICONTROL Chapter offset]](/help/reporting/dimensions/chapter-offset.md)
    * [[!UICONTROL Chapter position]](/help/reporting/dimensions/chapter-position.md)
    * [[!UICONTROL Originator]](/help/reporting/dimensions/originator.md)
  * **Metrics:**
    * [[!UICONTROL Chapter completes]](/help/reporting/metrics/chapter-completes.md)
    * [[!UICONTROL Chapter starts]](/help/reporting/metrics/chapter-starts.md)
    * [[!UICONTROL Chapter time spent]](/help/reporting/metrics/chapter-time-spent.md)
* **[!UICONTROL Media Quality]**: Enables tracking of playback quality data, including buffering, bitrate, and error events.
  * **Dimensions:**
    * [[!UICONTROL Average bitrate]](/help/reporting/dimensions/average-bitrate.md)
    * [[!UICONTROL Bitrate changes]](/help/reporting/dimensions/bitrate-changes.md)
    * [[!UICONTROL Buffer events]](/help/reporting/dimensions/buffer-events.md)
    * [[!UICONTROL Dropped frames]](/help/reporting/dimensions/dropped-frames.md)
    * [[!UICONTROL Errors]](/help/reporting/dimensions/errors.md)
    * [[!UICONTROL External error IDs]](/help/reporting/dimensions/external-error-ids.md)
    * [[!UICONTROL Player SDK error IDs]](/help/reporting/dimensions/player-sdk-error-ids.md)
    * [[!UICONTROL Time to start]](/help/reporting/dimensions/time-to-start.md)
    * [[!UICONTROL Total buffer duration]](/help/reporting/dimensions/total-buffer-duration.md)
  * **Metrics:**
    * [[!UICONTROL Average bitrate]](/help/reporting/metrics/average-bitrate.md)
    * [[!UICONTROL Bitrate change impacted streams]](/help/reporting/metrics/bitrate-change-impacted-streams.md)
    * [[!UICONTROL Bitrate changes]](/help/reporting/metrics/bitrate-changes.md)
    * [[!UICONTROL Buffer events]](/help/reporting/metrics/buffer-events.md)
    * [[!UICONTROL Buffer impacted streams]](/help/reporting/metrics/buffer-impacted-streams.md)
    * [[!UICONTROL Dropped frame impacted streams]](/help/reporting/metrics/dropped-frame-impacted-streams.md)
    * [[!UICONTROL Dropped frames]](/help/reporting/metrics/dropped-frames.md)
    * [[!UICONTROL Drops before start]](/help/reporting/metrics/drops-before-start.md)
    * [[!UICONTROL Error events]](/help/reporting/metrics/error-events.md)
    * [[!UICONTROL Error impacted streams]](/help/reporting/metrics/error-impacted-streams.md)
    * [[!UICONTROL Time to start]](/help/reporting/metrics/time-to-start.md)
    * [[!UICONTROL Total buffer duration]](/help/reporting/metrics/total-buffer-duration.md)
* **[!UICONTROL Video Metadata]**: Enables tracking of standard video content attributes such as show, season, and genre.
  * **Dimensions:**
    * [!UICONTROL Ad loads]
    * [[!UICONTROL Day part]](/help/reporting/dimensions/day-part.md)
    * [[!UICONTROL Episode]](/help/reporting/dimensions/episode.md)
    * [[!UICONTROL Genre]](/help/reporting/dimensions/genre.md)
    * [[!UICONTROL Media feed type]](/help/reporting/dimensions/media-feed-type.md)
    * [[!UICONTROL MVPD]](/help/reporting/dimensions/mvpd.md)
    * [[!UICONTROL Network]](/help/reporting/dimensions/network.md)
    * [[!UICONTROL Season]](/help/reporting/dimensions/season.md)
    * [[!UICONTROL Show]](/help/reporting/dimensions/show.md)
    * [[!UICONTROL Show type]](/help/reporting/dimensions/show-type.md)
  * **Metric:**
    * [[!UICONTROL Authorized]](/help/reporting/metrics/authorized.md)
* **[!UICONTROL Audio Metadata]**: Enables tracking of standard audio content attributes such as artist, album, and station.
  * **Dimensions:**
    * [[!UICONTROL Album]](/help/reporting/dimensions/album.md)
    * [[!UICONTROL Artist]](/help/reporting/dimensions/artist.md)
    * [[!UICONTROL Author]](/help/reporting/dimensions/author.md)
    * [[!UICONTROL Label]](/help/reporting/dimensions/label.md)
    * [[!UICONTROL Publisher]](/help/reporting/dimensions/publisher.md)
    * [[!UICONTROL Station]](/help/reporting/dimensions/station.md)
* **[!UICONTROL Player State Tracking]**: Enables measurement of standard player UI states such as full screen, closed captioning, and picture in picture.
  * **Metrics:**
    * [[!UICONTROL Closed captioning counts]](/help/reporting/metrics/closed-captioning-count.md)
    * [[!UICONTROL Closed captioning total duration]](/help/reporting/metrics/closed-captioning-total-duration.md)
    * [[!UICONTROL Full screen counts]](/help/reporting/metrics/full-screen-count.md)
    * [[!UICONTROL Full screen total duration]](/help/reporting/metrics/full-screen-total-duration.md)
    * [[!UICONTROL In focus counts]](/help/reporting/metrics/in-focus-count.md)
    * [[!UICONTROL In focus total duration]](/help/reporting/metrics/in-focus-total-duration.md)
    * [[!UICONTROL Mute counts]](/help/reporting/metrics/mute-count.md)
    * [[!UICONTROL Mute total duration]](/help/reporting/metrics/mute-total-duration.md)
    * [[!UICONTROL Picture in picture counts]](/help/reporting/metrics/picture-in-picture-count.md)
    * [[!UICONTROL Picture in picture total duration]](/help/reporting/metrics/picture-in-picture-total-duration.md)
    * [[!UICONTROL Streams impacted by closed captioning]](/help/reporting/metrics/closed-captioning-streams-impacted.md)
    * [[!UICONTROL Streams impacted by full screen]](/help/reporting/metrics/full-screen-streams-impacted.md)
    * [[!UICONTROL Streams impacted by in focus]](/help/reporting/metrics/in-focus-streams-impacted.md)
    * [[!UICONTROL Streams impacted by mute]](/help/reporting/metrics/mute-streams-impacted.md)
    * [[!UICONTROL Streams impacted by picture in picture]](/help/reporting/metrics/picture-in-picture-streams-impacted.md)
