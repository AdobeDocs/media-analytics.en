---
title: Learn How to Track Ads on Android
description: Implement ad tracking in Android applications using the Media SDK.
uuid: 4a4249fb-dc39-4947-a14d-a51d972f32d4
exl-id: 1f96dde9-c924-4fce-8b14-7dec7137f265
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/9TbZkzhIR-b4nvKcVgmCAKsvN-nljf3YCDNPNEUA4yI
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
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
# Track ads on Android{#track-ads-on-android}

The following instructions provide guidance for implementation using the 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Ad tracking constants

|  Constant&nbsp;name  | Description |
| --- | --- |
|  `MediaHeartbeat.Event.AdBreakStart`  | Constant for tracking AdBreak Start event  |
|  `MediaHeartbeat.Event.AdBreakComplete`  | Constant for tracking AdBreak Complete event  |
|  `MediaHeartbeat.Event.AdStart`  | Constant for tracking Ad Start event  |
|  `MediaHeartbeat.Event.AdComplete`  | Constant for tracking Ad Complete event  |
|  `MediaHeartbeat.Event.AdSkip`  | Constant for tracking Ad Skip event  |

## Implementation steps

1. Identify when the ad break boundary begins, including pre-roll, and create an `AdBreakObject` by using the ad break information.

   `AdBreakObject` reference:

   |  Variable Name  | Description  | Required  |
   | --- | --- | :---: |
   |  `name`  | Ad break name such as pre-roll, mid-roll, and post-roll.  | Yes  |
   |  `position`  | The number position of the ad break within the content, starting with 1. | Yes  |
   |  `startTime`  | Playhead value at the start of the ad break.  | Yes  |

   Ad break object creation:

   ```java
   MediaObject adBreakInfo =  
     MediaHeartbeat.createAdBreakObject(<ADBREAK_NAME>,  
                                        <POSITION>,  
                                        <START_TIME>);
   ```

1. Call `trackEvent()` with `AdBreakStart` in the `MediaHeartbeat` instance to begin tracking the ad break:

   ```java
   public void onAdBreakStart(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.AdBreakStart,  
                             adBreakInfo,  
                             null);
   }
   ```

1. Identify when the ad starts and create an `AdObject` instance using the ad information.

   `AdObject` reference:

   |  Variable Name  | Description  | Required  |
   | --- | --- | :---: |
   |  `name`  | Friendly name of the ad.  | Yes  |
   |  `adId`  | Unique identifier for the ad.  | Yes  |
   |  `position`  | The number position of the ad within the ad break, starting with 1. | Yes  |
   |  `length`  | Ad length  | Yes  |

   Ad object creation:

   ```java
   MediaObject adInfo =  
     MediaHeartbeat.createAdObject(<AD_NAME>
                                   <AD_ID>,  
                                   <POSITION>,  
                                   <LENGTH>);
   ```

1. Optionally attach standard and/or ad metadata to the media tracking session through context data variables.

    * [Implement standard ad metadata on Android](/help/use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-metadata-android.md)

    help/use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-metadata-android.md

    * **Custom ad metadata -** For custom metadata, create a variable object for the custom data variables and populate with the data for the current ad:     

      ```java    
      // Setting Ad Metadata
      HashMap<String, String> adMetadata = new HashMap<String, String>();
      adMetadata.put("affiliate", "Sample affiliate");
      adMetadata.put("campaign", "Sample ad campaign");
      ```

1. Call `trackEvent()` with the `AdStart` event in the `MediaHeartbeat` instance to begin tracking the ad playback.

   Include a reference to your custom metadata variable (or an empty object) as the third parameter in the event call:

   ```java
   public void onAdStart(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.AdStart,  
                             adInfo,  
                             adMetadata);
   }
   ```

1. When the ad playback reaches the end of the ad, call `trackEvent()` with the `AdComplete` event:

   ```java
   public void onAdComplete(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.AdComplete, null, null);
   }
   ```

1. If ad playback did not complete because the user chose to skip the ad, track the `AdSkip` event:

   ```java
   public void onAdSkip(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.AdSkip, null, null);
   }
   ```

1. If there are any additional ads within the same `AdBreak`, repeat steps 3 through 7 again.
1. When the ad break is complete, use the `AdBreakComplete` event to track:

   ```java
   public void onAdBreakComplete(Observable observable, Object data) {  
       _heartbeat.trackEvent(MediaHeartbeat.Event.AdBreakComplete, null, null);
   }
   ```

See the tracking scenario [VOD playback with pre-roll ads](/help/use-cases/tracking-scenarios/vod-preroll-ads.md) for more information.
