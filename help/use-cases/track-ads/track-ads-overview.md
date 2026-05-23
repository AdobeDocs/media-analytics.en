---
title: Track Ads Explained
description: Overview of implementing ad tracking with the Media SDK.
uuid: 1607798b-c6ef-4d60-8e40-e958c345b09c
exl-id: c714d31f-3d08-4ded-a413-2762d53bec75
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/PguxKIzAL95WbMl5c0yJq9rYSqZgOGbbAYtxOI4eVOs
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Overview{#overview}

The following instructions provide guidance for implementation using the 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

Ad playback includes tracking ad breaks, ad starts, ad completes, and ad skips. Use the media player's API to identify key player events and to populate the required and optional ad variables.

## Player events {#player-events}

### On ad break start

>[!NOTE]
>Including pre-roll

* Create an `adBreak` object instance for the ad break. For example, `adBreakObject`.

* Call `trackEvent` for the ad break start with your `adBreakObject`.

### On every ad asset start

* Create an ad object instance for the ad asset. For example, `adObject`.
* Populate the ad metadata, `adCustomMetadata`.
* Call `trackEvent` for the ad start.

### On every ad complete

* Call `trackEvent` for the ad complete.

### On ad skip

* Call `trackEvent` for the ad skip.

### On ad break complete

* Call `trackEvent` for the ad break complete.

## Implement ad tracking {#implement-ad-tracking}

### Ad tracking constants

|  Constant name  | Description&nbsp;&nbsp;  |
|---|---|
|  `AdBreakStart`  | Constant for tracking AdBreak Start event  |
|  `AdBreakComplete`  | Constant for tracking AdBreak Complete event  |
|  `AdStart`  | Constant for tracking Ad Start event  |
|  `AdComplete`  | Constant for tracking Ad Complete event  |
|  `AdSkip`  | Constant for tracking Ad Skip event  |

### Implementation steps

1. Identify when the ad break boundary begins, including pre-roll, and create an `AdBreakObject` by using the ad break information.

   `AdBreakObject` reference:

   |  Variable Name  | Description  | Required  |
   | --- | --- | :---: |
   |  `name`  | Ad break name such as pre-roll, mid-roll, and post-roll.  | Yes  |
   |  `position`  | The number position of the ad break within the content, starting with 1. | Yes  |
   |  `startTime`  | Playhead value at the start of the ad break.  | Yes  |

1. Call `trackEvent()` with `AdBreakStart` in the `MediaHeartbeat` instance to begin tracking the ad break.

1. Identify when the ad starts and create an `AdObject` instance using the ad information.

   `AdObject` reference:

   |  Variable Name  | Description  | Required  |
   | --- | --- | :---: |
   |  `name`  | Friendly name of the ad.  | Yes  |
   |  `adId`  | Unique identifier for the ad.  | Yes  |
   |  `position`  | The number position of the ad within the ad break, starting with 1. | Yes  |
   |  `length`  | Ad length  | Yes  |

1. Optionally attach standard and/or ad metadata to the tracking session through context data variables.

    * **Standard ad metadata -** For standard ad metadata, create a dictionary of standard ad metadata key value pairs using the keys for your platform.
    * **Custom ad metadata -** For custom metadata, create a variable object for the custom data variables and populate with the data for the current ad.

1. Call `trackEvent()` with the `AdStart` event in the `MediaHeartbeat` instance to begin tracking the ad playback.

   Include a reference to your custom metadata variable (or an empty object) as the third parameter in the event call. While the ad is playing, keep the content playhead (`l:event:playhead`) fixed at the position where the ad break began; advancing it during ad playback overstates [Content time spent](/help/reporting/metrics/content-time-spent.md).

1. When the ad playback reaches the end of the ad, call `trackEvent()` with the `AdComplete` event.

1. If ad playback did not complete because the user chose to skip the ad, track the `AdSkip` event.
1. If there are any additional ads within the same `AdBreak`, repeat steps 3 through 7 again.
1. When the ad break is complete, use the `AdBreakComplete` event to track it.

>[!IMPORTANT]
>
>**Pre-roll ads: do not call `trackPlay` before `AdBreakStart` and `AdStart`.** The first `play` ping on main content increments [Content starts](/help/reporting/metrics/content-starts.md). If `trackPlay` is called before the pre-roll ad events fire and the viewer drops out during the ad, Content starts is incremented even though no main content was ever played. For pre-roll scenarios, delay `trackPlay` until after `AdBreakStart` and `AdStart` have been sent.

>[!NOTE]
>
>The playhead value reported during ad playback represents the viewer's position within the **main content**, not within the ad. For a pre-roll ad preceding a 10-minute video, the playhead is `0` throughout the entire ad. For a mid-roll ad that starts at the 5-minute mark, the playhead remains at `300` (seconds) for the duration of the ad.

The following sample code utilizes the JavaScript 2.x SDK for an HTML5 media player.

```js
/* Call on ad break start */

if (e.type == "ad break start") {
    var adBreakObject = MediaHeartbeat.createAdBreakObject("mid-roll", 2, 500);
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart, adBreakObject);
};

/* Call on ad start */
if (e.type == "ad start") {
    var adObject = MediaHeartbeat.createAdObject("PepsiOne", "123456ab", 1, 30);
    /* Set custom context data */
    var adCustomMetadata = {
        affiliate:"Sample affiliate",
        campaign:"Sample ad campaign",
        creative:"Sample creative"
    }
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdStart, adObject, adCustomMetadata);
};

/* Call on ad complete */
if (e.type == "ad complete") {
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdComplete);
};

/* Call on ad skip */
if (e.type == "ad skip") {
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdSkip);
};

/* Call on ad break complete */
if (e.type == "ad break complete") {
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete);
};
```

>[!MORELIKETHIS]
>
>* [Ad break start](/help/implementation/events/ads/ad-break-start.md)
>* [Ad start](/help/implementation/events/ads/ad-start.md)
>* [Ad complete](/help/implementation/events/ads/ad-complete.md)
>* [Ad skip](/help/implementation/events/ads/ad-skip.md)
>* [Ad break complete](/help/implementation/events/ads/ad-break-complete.md)
