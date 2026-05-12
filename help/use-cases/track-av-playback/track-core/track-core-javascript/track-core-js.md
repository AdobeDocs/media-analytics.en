---
title: Learn How To Track Core Playback Using JavaScript 2.x
description: Learn how to implement core tracking using the Media SDK in a browser using JavaScript 2.x apps.
uuid: 3d6e0ab1-899a-43c3-b632-8276e84345ab
exl-id: d8af37a0-9048-4e6b-8cba-809386cbed5f
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/efxauhuL5aOcMQhSuayeodzUOtgfppMgZTAiwTiHsEE
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
# Track core playback using JavaScript 2.x{#track-core-playback-on-javascript}

The following instructions provide guidance for implementation across 2.x SDKs.

>[!IMPORTANT]
>If you are implementing a 1.x version of the SDK, you can download 1.x Developers Guides here: [Download SDKs](/help/getting-started/download-sdks.md)

1. **Initial tracking setup**

    Identify when the user triggers the intention of playback (the user clicks play and/or autoplay is on) and create a `MediaObject` instance.

    [createMediaObject API](https://adobe-marketing-cloud.github.io/media-sdks/reference/javascript/MediaHeartbeat.html#.createMediaObject)

    |  Variable Name  | Description  | Required  |
    | --- | --- | :---: |
    |  `name`  | Media name  | Yes  |
    |  `mediaid`  | Media unique identifier  | Yes  |
    |  `length`  | Media length  | Yes  |
    |  `streamType`  | Stream type (see _StreamType constants_ below)  | Yes  |
    |  `mediaType`  | Media type (see _MediaType constants_ below)  | Yes  |

    **`StreamType` constants:**

    |  Constant Name  | Description&nbsp;&nbsp;  |
    |---|---|
    |  `VOD`  | Stream type for Video on Demand.  |
    |  `LIVE`  | Stream type for LIVE content.  |
    |  `LINEAR`  | Stream type for LINEAR content.  |
    |  `AOD`  | Stream type for Audio on Demand.  |
    |  `AUDIOBOOK`  | Stream type for Audio Book.  |
    |  `PODCAST`  | Stream type for Podcast.  |

    **`MediaType` constants:**

    |  Constant Name  | Description  |
    |---|---|
    |  `Audio`  | Media type for Audio streams.  |
    |  `Video`  | Media type for Video streams.  |

    ```
    var mediaObject =  
      MediaHeartbeat.createMediaObject(<MEDIA_NAME>,  
                                      <MEDIA_ID,  
                                      <MEDIA_LENGTH>,
                                      MediaHeartbeat.StreamType.VOD,
                                      <MEDIA_TYPE>);
    ```

1. **Attach metadata**

    Optionally attach standard and/or custom metadata objects to the tracking session through context data variables.

    * **Standard metadata**

       [Implement standard metadata on JavaScript](/help/use-cases/track-av-playback/impl-std-metadata/impl-std-md-js/impl-std-metadata-js.md)     

       >[!NOTE]
       >
       >Attaching the standard metadata object to the media object is optional.

       * Media metadata keys API Reference - [Standard metadata keys - JavaScript](https://adobe-marketing-cloud.github.io/media-sdks/reference/javascript)

    * **Custom metadata**

       Create a variable object for the custom variables and populate with the data for this media. For example:     

       ```js
       /* Set custom context data */
       var customVideoMetadata = {
           isUserLoggedIn: "false",
           tvStation: "Sample TV station",
           programmer: "Sample programmer"
       };
       ```

1. **Track the intention to start playback**

    To begin tracking a media session, call `trackSessionStart` on the Media Heartbeat instance:

    ```js
    mediaHeartbeat.trackSessionStart(mediaObject, customVideoMetadata);
    ```

    >[!TIP]
    >
    >The second value is the custom media metadata object name that you created in step 2.

    >[!IMPORTANT]
    >
    >`trackSessionStart` tracks the user intention of playback, not the beginning of the playback. This API is used to load the data/metadata and to estimate the time-to-start QoS metric (the time duration between `trackSessionStart` and `trackPlay`).

    >[!NOTE]
    >
    >If you are not using custom metadata, simply send an empty object for the `data` argument in `trackSessionStart`, as shown in the commented out line in the iOS example above.

1. **Track the actual start of playback**

    Identify the event from the media player for the beginning of the playback, where the first frame of the media is rendered on the screen, and call `trackPlay`:

    ```js
    mediaHeartbeat.trackPlay();
    ```

1. **Track the completion of playback**

    Identify the event from the media player for the completion of the playback, where the user has watched the content until the end, and call `trackComplete`:

    ```js
    mediaHeartbeat.trackComplete();
    ```

1. **Track the end of the session**

    Identify the event from the media player for the unloading/closing of the playback, where the user closes the media and/or the media is completed and has been unloaded, and call `trackSessionEnd`:

    ```js
    mediaHeartbeat.trackSessionEnd();
    ```

    >[!IMPORTANT]
    >
    >`trackSessionEnd` marks the end of a tracking session. If the session was successfully watched to completion, where the user watched the content until the end, ensure that `trackComplete` is called before `trackSessionEnd`. Any other `track*` API call is ignored after `trackSessionEnd`, except for `trackSessionStart` for a new tracking session.

1. **Track all possible pause scenarios**

    Identify the event from the media player for pause and call `trackPause`:

    ```js
    mediaHeartbeat.trackPause();
    ```

    **Pause Scenarios**

    Identify any scenario in which the media player will pause and make sure that `trackPause` is properly called. The following scenarios all require that your app call `trackPause()`:

    * The user explicitly hits pause in the app.
    * The player puts itself into the Pause state.
    * (*Mobile Apps*) - The user puts the application into the background, but you want the app to keep the session open.
    * (*Mobile Apps*) - Any type of system interrupt occurs that causes an application to be backgrounded. For example, the user receives a call, or a pop up from another application occurs, but you want the application to keep the session alive to give the user the opportunity to resume the media from the point of interruption.

1. Identify the event from the player for play and/or resume from pause and call `trackPlay`:

    ```js
    mediaHeartbeat.trackPlay();
    ```

    >[!TIP]
    >
    >This may be the same event source that was used in Step 4. Ensure that each `trackPause()` API call is paired with a following `trackPlay()` API call when the playback resumes.

* Tracking scenarios: [VOD playback with no ads](/help/use-cases/tracking-scenarios/vod-no-intrs-details.md)
* Sample player included with the JavaScript SDK for a complete tracking example.
