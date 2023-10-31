---
title: Learn How to Track Ads Using JavaScript 3.x
description: Implement ad tracking in browser (JS) applications using the Media SDK.
exl-id: 6b34b2c0-5e50-471a-b52c-b9c760fa3169
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Track ads using JavaScript 3.x{#track-ads-on-javascript}

The following instructions provide guidance for implementation using the 3.x SDKs.

>[!IMPORTANT]
>
>If you are implementing any previous versions of the SDK, you can download the Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Ad tracking constants

|  Constant name  | Description&nbsp;&nbsp;  |
|---|---|
|  `AdBreakStart`  | Constant for tracking AdBreak Start event  |
|  `AdBreakComplete`  | Constant for tracking AdBreak Complete event  |
|  `AdStart`  | Constant for tracking Ad Start event  |
|  `AdComplete`  | Constant for tracking Ad Complete event  |
|  `AdSkip`  | Constant for tracking Ad Skip event  |

## Implementation steps

1. Identify when the ad break boundary begins, including pre-roll, and create an `AdBreakObject` by using the ad break information.

   `AdBreakObject` reference:

   | Variable Name | Type | Description |
   | --- | --- | --- |
   | `name` | string | Non empty string denoting adbreak name (pre-roll, mid-roll, and post-roll).  |
   | `position` | number | The number position of the ad break starting with 1.  |
   | `startTime` | number | Playhead value at the start of the ad break.  |

   Ad break object creation:

   ```js
   var adBreakObject =
     ADB.Media.createAdBreakObject(<ADBREAK_NAME>,
                                      <POSITION>,
                                      <START_TIME>);
   ```

1. Call `trackEvent()` with `AdBreakStart` in the `MediaHeartbeat` instance to begin tracking the ad break:

   ```js
   tracker.trackEvent(ADB.Media.Event.AdBreakStart, adBreakObject);
   ```

1. Identify when the ad starts and create an `AdObject` instance using the ad information.

   `AdObject` reference:

   |  Variable Name  | Type | Description  |
   | --- | --- | --- |
   |  `name`  | string | Non empty string denoting ad name.  |
   |  `adId`  | string | Non empty string denoting ad identifier.  |
   |  `position`  | number | The number position of the ad within the adbreak, starting with 1. |
   |  `length`  | number | Positive number denoting length of the ad.  |

   Ad object creation:

   ```js
   var adObject =
     ADB.Media.createAdObject.createAdObject(<AD_NAME>,
                                   <AD_ID>,
                                   <POSITION>,
                                   <LENGTH>);
   ```

1. (Optional) Attach standard and/or ad metadata to the media tracking session through context data variables.

    * [Implement standard ad metadata on JavaScript](/help/use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-md-js/impl-std-ad-metadata-js3.md)
    * **Custom ad metadata -** For custom metadata, create a variable object for the custom data variables and populate with the data for the current ad:

      ```js
      /* Set context data */
      // Standard metadata keys provided by adobe.
      adMetadata[ADB.Media.AdMetadataKeys]  ="Sample Advertiser";
      adMetadata[ADB.Media.AdMetadataKeys] = "Sample Campaign";

      // Custom metadata keys
      adMetadata["affiliate"] = "Sample affiliate";
      adMetadata["campaign"] = "Sample ad campaign";
      adMetadata["creative"] = "Sample creative";
      ```

1. (Optional) Set up granular ad tracking to enable `1 second` ad tracking.

   This information must be provided when starting a tracking session.

   >[!NOTE]
   >
   >   The default ad ping interval is `10 seconds`.


   **Syntax**

   ```javascript
    ADB.Media.MediaObjectKey = {
       GranularAdTracking: "media.granularadtracking"
   }
   ```

   **Example**

   ```javascript
   var mediaObject = ADB.Media.createMediaObject("media-name", "media-id", 60, ADB.Media.StreamType.VOD, ADB.Media.MediaType.Video);

   // Enable granular ad tracking
   mediaObject[ADB.Media.MediaObjectKey.GranularAdTracking] = true;

   tracker.trackSessionStart(mediaObject);
   ```

1. Call `trackEvent()` with the `AdStart` event in the `MediaHeartbeat` instance to begin tracking the ad playback.

   Include a reference to your custom metadata variable (or an empty object) as the third parameter in the event call:

   ```js
   _onAdStart = function() {
       tracker.trackEvent(ADB.Media.Event.AdStart, adObject, adMetadata);
   };
   ```

1. When the ad playback reaches the end of the ad, call `trackEvent()` with the `AdComplete` event:

   ```js
   _onAdComplete = function() {
       tracker.trackEvent(ADB.Media.Event.AdComplete);
   };
   ```

1. If ad playback did not complete because the user chose to skip the ad, track the `AdSkip` event:

   ```js
   _onAdSkip = function() {
       tracker.trackEvent(ADB.Media.Event.AdSkip);
   };
   ```

1. If there are any additional ads within the same `AdBreak`, repeat steps 3 through 7 again.
1. When the ad break is complete, use the `AdBreakComplete` event to track:

   ```js
   _onAdBreakComplete = function() {
       tracker.trackEvent(ADB.Media.Event.AdBreakComplete);
   };
   ```

See the tracking scenario [VOD playback with pre-roll ads](/help/use-cases/tracking-scenarios/vod-preroll-ads.md) for more information.
