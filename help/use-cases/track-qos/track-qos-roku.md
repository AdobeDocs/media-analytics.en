---
title: Learn How to Track Quality of Experience on Roku
description: Learn about implementing quality of experience (QoE, QoS) tracking using the Media SDK on Roku.
uuid: a8b242ab-da3c-4297-9eef-f0b9684ef56a
exl-id: cd84c26d-ad91-4179-9532-83408030ff3e
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/-e2JKBn8IB9Kk-MEVIlQq6IY5Wuevlp6GrpkM96xuX4
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Track quality of experience on Roku{#track-quality-of-experience-on-roku}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

## Implement QOS

1. Identify when the bitrate changes during media playback, and use the `mediaUpdateQoS` API to update the QoS info on the Media SDK.

    QoSObject variables:

    >[!TIP]
    >
    >These variables are only required if you are tracking QoS.

    | Variable | Description | Required |
    | --- | --- | :---: |
    | `bitrate` | Current bitrate | Yes |
    | `startupTime` | Startup time | Yes |
    | `fps` | FPS value | Yes |
    | `droppedFrames` | Number of dropped frames | Yes |

    For example:

    ```
    bitrate = 200000
    fps = 0
    droppedFrames = 1
    startupTime = 2
    qosinfo = adb_media_init_qosinfo(bitrate, startupTime, fps, droppedFrames)

    ADBMobile().mediaUpdateQoS(qosinfo)
    ```

    <!--
    QoS object creation:

    ```
    qosInfo=adb_media_init_qosinfo()
    qosInfo.bitrate = 200000
    qosInfo.fps = 0
    qosInfo.droppedFrames = 1
    qosInfo.startupTime = 2
    ```
    -->

1. When playback switches bitrates, call `trackEvent(BitrateChange)` to notify the Media SDK that the Bitrate changed.

    ```
    ADBMobile().mediaTrackEvent(ADBMobile().MEDIA_BITRATE_CHANGE)
    ```

    >[!NOTE]
    >
    >You need to call `updateQoSObject` with the updated bitrate value.

    <!--
    ```
    qosContextData = {}
    ADBMobile().mediaTrackEvent(MEDIA_BITRATE_CHANGE, qosInfo, qosContextData)
    ```

    >[!IMPORTANT]
    >
    >Update the QoS object and call the bitrate change event on every bitrate change. This provides the most accurate QoS data.
    -->

1. When the media player encounters an error, and the error event is available to the player API, use `trackError()` to capture the error information. (See [Overview](/help/use-cases/track-errors/track-errors-overview.md).)

    >[!TIP]
    >
    >Tracking media player errors will not stop the media tracking session. If the media player error prevents the playback from continuing, make sure that the media tracking session is closed by calling `trackSessionEnd()` after calling `trackError()`.
