---
title: Learn How to Track Quality of Experience on Chromecast
description: Learn about implementing quality of experience (QoE, QoS) tracking using the Media SDK on Chromecast.
uuid: d0cdc8cd-4db0-45ef-9470-1cba3996305b
exl-id: 04b9b888-2727-4aa6-a934-94a02c85a490
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/VR-udMMg3tOMsbxnt-f0zjkGVZNgnCON0diYrhhMuoE
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Track quality of experience on Chromecast{#track-quality-of-experience-on-chromecast}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Overview {#overview}

Quality of experience tracking includes quality of service (QoS) and error tracking, both are optional elements and are **not** required for core media tracking implementations. You can use the media player API to identify the variables related to QoS and error tracking.

## Player events {#player-events}

### On all bitrate change events

* Create/update the QoS object instance for the playback, `qosObject`
* Call `trackEvent(Media.Heartbeat.Event.BitrateChange, qosObject);`

### On player errors

Call `trackError("media error id");`

## Implement {#implement}

1. Identify when the bitrate changes during media playback and create the `MediaObject` instance using the QoS information.

    **QoSObject variables:**

    >[!TIP]
    >
    >These variables are only required if you are planning to track QoS.

    | Variable | Description | Required |
    | --- | --- | :---: |
    | `bitrate` | Current bitrate | Yes |
    | `startupTime` | Startup time | Yes |
    | `fps` | FPS value | Yes |
    | `droppedFrames` | Number of dropped frames | Yes |

    **QoS object creation:** [createQoSObject](https://adobe-marketing-cloud.github.io/media-sdks/reference/chromecast/ADBMobile.media.html#.createQoSObject)

    ```
    qosInfo = ADBMobile.media.createQoSObject(50000, 0, 24, 10);
    ```

1. When playback switches bitrates, call the `BitrateChange` event in the Media Heartbeat instance: [trackEvent](https://adobe-marketing-cloud.github.io/media-sdks/reference/chromecast/ADBMobile.media.html#.trackEvent)

    ```
    ADBMobile.media.trackEvent(ADBMobile.media.Event.BitrateChange);
    ```

    >[!IMPORTANT]
    >
    >Update the QoS object and call the bitrate change event on every bitrate change. This provides the most accurate QoS data.

1. Make sure that `getQoSObject()` method returns the most updated QoS information.
1. When the media player encounters an error, and the error event is available to the player API, use `trackError()` to capture the error information. (See [Overview](/help/use-cases/track-errors/track-errors-overview.md).)

   >[!TIP]
   >
   >Tracking media player errors will not stop the media tracking session. If the media player error prevents the playback from continuing, make sure that the media tracking session is closed by calling `trackSessionEnd()` after calling `trackError()`.
