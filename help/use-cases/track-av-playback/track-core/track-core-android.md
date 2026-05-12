---
title: Learn How To Track Core Playback on Android
description: Learn how to implement core tracking using the Media SDK on Android.
uuid: ab5fab95-76ed-4ae6-aedb-2e66eece7607
exl-id: d5f5a3f0-f1e0-4d68-af7f-88a30faed0db
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/W-wkhWebsd4z-eOWdqeyZgxrH4ztckDVyHejylpfkHI
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
# Track core playback on Android{#track-core-playback-on-android}

This documentation covers tracking in version 2.x of the SDK.
>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guide for Android here: [Download SDKs](/help/getting-started/download-sdks.md)

1. **Initial tracking setup**

    Identify when the user triggers the intention of playback (the user clicks play and/or autoplay is on) and create a `MediaObject` instance.

    [createMediaObject API](https://adobe-marketing-cloud.github.io/media-sdks/reference/android/com/adobe/primetime/va/simple/MediaHeartbeat.html#createMediaObject-java.lang.String-java.lang.String-java.lang.Double-java.lang.String-com.adobe.primetime.va.simple.MediaHeartbeat.MediaType-)

    |  Variable Name  | Description  | Required  |
    | --- | --- | :---: |
    |  `name`  | Media name  | Yes  |
    |  `mediaId`  | Media unique identifier  | Yes  |
    |  `length`  | Media length  | Yes  |
    |  `streamType`  | Stream type (see _StreamType constants_ below)  | Yes  |
    |  `mediaType`  | Media type (see _MediaType constants_ below)  | Yes  |

    **`StreamType` constants:**

    |  Constant Name  | Description  |
    |---|---|
    |  `VOD`  | Stream type for Video on Demand.  |
    |  `LIVE`  | Stream type for Live content.  |
    |  `LINEAR`  | Stream type for Linear content.  |
    |  `AOD`  | Stream type for Audio On Demand  |
    |  `AUDIOBOOK`  | Stream type for Audio Book  |
    |  `PODCAST`  | Stream type for Podcast  |

    **`MediaType` constants:**

    |  Constant Name  | Description  |
    |---|---|
    |  `Audio`  | Media type for Audio streams.  |
    |  `Video`  | Media type for Video streams.  |

    ```
    MediaHeartbeat.createMediaObject(<MEDIA_NAME>,  
      <MEDIA_ID>, <MEDIA_LENGTH>, <STREAM_TYPE>, <MEDIA_TYPE>);
    ```

1. **Attach metadata**

    Optionally attach standard and/or custom metadata objects to the tracking session through context data variables.

    * **Standard metadata**

       [Implement standard metadata on Android](/help/use-cases/track-av-playback/impl-std-metadata/impl-std-metadata-android.md)     

      >[!NOTE]
      >
      >Attaching the standard metadata object to the media object is optional.

        * Media metadata keys API Reference - [Standard metadata keys - Android](https://adobe-marketing-cloud.github.io/media-sdks/reference/android/com/adobe/primetime/va/simple/MediaHeartbeat.VideoMetadataKeys.html)

    * **Custom metadata**

       Create a dictionary for the custom variables and populate with the data for this media. For example:     

      ```java    
      HashMap<String, String> mediaMetadata =  
        new HashMap<String, String>();
      mediaMetadata.put("isUserLoggedIn", "false");
      mediaMetadata.put("tvStation", "Sample TV Station");
      mediaMetadata.put("programmer", "Sample programmer");
      ```

1. **Track the intention to start playback**

    To begin tracking a media session, call `trackSessionStart` on the Media Heartbeat instance. For example:

   ```java
   public void onVideoLoad(Observable observable, Object data) {  
       _heartbeat.trackSessionStart(mediaInfo, mediaMetadata);
   }
   ```

   >[!TIP]
   >
   >The second value is the custom media metadata object name that you created in step 2.

   >[!IMPORTANT]
   >
   >`trackSessionStart` tracks the user intention of playback, not the beginning of the playback. This API is used to load the media data/metadata and to estimate the time-to-start QoS metric (the time duration between `trackSessionStart` and `trackPlay`).

   >[!NOTE]
   >
   >If you are not using custom media metadata, simply send an empty object for the second argument in `trackSessionStart`.

1. **Track the actual start of playback**

    Identify the event from the media player for the beginning of the media playback, where the first frame of the media is rendered on the screen, and call `trackPlay`:

   ```java
   // Video is rendered on the screen) and call trackPlay.  
   public void onVideoPlay(Observable observable, Object data) {
       _heartbeat.trackPlay();
   }
   ```

1. **Track the completion of playback**

    Identify the event from the media player for the completion of the media playback, where the user has watched the content until the end, and call `trackComplete`:

   ```java
   public void onVideoComplete(Observable observable, Object data) {
       _heartbeat.trackComplete();
   }
   ```

1. **Track the end of the session**

    Identify the event from the media player for the unloading/closing of the media playback, where the user closes the media and/or the media is completed and has been unloaded, and call `trackSessionEnd`:

   ```java
   // Closes the media and/or the media completed and unloaded,  
   // and call trackSessionEnd().  
   public void onMainVideoUnload(Observable observable, Object data) {  
       _heartbeat.trackSessionEnd();
   }
   ```

   >[!IMPORTANT]
   >
   >`trackSessionEnd` marks the end of a media tracking session. If the session was successfully watched to completion, where the user watched the content until the end, ensure that `trackComplete` is called before `trackSessionEnd`. Any other `track*` API call is ignored after `trackSessionEnd`, except for `trackSessionStart` for a new media tracking session.

1. **Track all possible pause scenarios**

    Identify the event from the media player for media pause and call `trackPause`:

   ```java
   public void onVideoPause(Observable observable, Object data) {  
       _heartbeat.trackPause();
   }
   ```

   **Pause Scenarios**

   Identify any scenario in which the Video Player will pause and make sure that `trackPause` is properly called. The following scenarios all require that your app call `trackPause()`:

    * The user explicitly hits pause in the app.
    * The player puts itself into the Pause state.
    * (*Mobile Apps*) - The user puts the application into the background, but you want the app to keep the session open.
    * (*Mobile Apps*) - Any type of system interrupt occurs that causes an application to be backgrounded. For example, the user receives a call, or a pop up from another application occurs, but you want the application to keep the session alive to give the user the opportunity to resume the media from the point of interruption.

1. Identify the event from the player for media play and/or media resume from pause and call `trackPlay`.

   ```java
   // trackPlay()
   public void onVideoPlay(Observable observable, Object data) {  
       _heartbeat.trackPlay();
   }
   ```

   >[!TIP]
   >
   >This may be the same event source that was used in Step 4. Ensure that each `trackPause()` API call is paired with a following `trackPlay()` API call when the media playback resumes.

See the following for additional information on tracking core playback:

* Tracking scenarios: [VOD playback with no ads](/help/use-cases/tracking-scenarios/vod-no-intrs-details.md)
* Sample player included with the Android SDK for a complete tracking example.
