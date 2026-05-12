---
title: Track Quality of Experience Explained
description: An overview of tracking quality of experience (QoE, QoS) using the Media SDK.
uuid: 4d73c47f-d0a4-4228-9040-d6432311c9eb
exl-id: af5f3372-a9a5-46ea-9c2f-81b0f5c96ccf
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/Cc5T13Z1S15MyG-CxpxMoHX-ckULmIe0dfUOe7650DE
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Overview{#overview}

The following instructions provide guidance for implementation across all 2.x SDKs.

>[!IMPORTANT]
>
>If you are implementing a 1.x version of the SDK, you can download the 1.x Developers Guides here: [Download SDKs.](/help/getting-started/download-sdks.md)

Quality of experience tracking includes quality of service (QoS) and error tracking, both are optional elements and are **not** required for core media tracking implementations. You can use the media player API to identify the variables related to QoS and error tracking. Here are the key elements of tracking quality of experience:

## Player events {#player-events}

### On any QoS metric changes:

Create or update the QoS object instance for the playback. [QoS API Reference](https://adobe-marketing-cloud.github.io/media-sdks/reference/javascript/MediaHeartbeat.html#.createQoSObject)

### On all bitrate change events

Call `trackEvent(Media.Heartbeat.Event.BitrateChange);`

## Implement QOS

1. Identify when any of QOS metrics change during media playback, create the `MediaObject` using the QoS information, and update the new QoS information.

    QoSObject variables:

    >[!TIP]
    >
    >These variables are only required if you are planning to track QoS.

    | Variable | Description | Required |
    | --- | --- | :---: |
    | `bitrate` | Current bitrate | Yes |
    | `startupTime` | Startup time | Yes |
    | `fps` | FPS value | Yes |
    | `droppedFrames` | Number of dropped frames | Yes |

1. Make sure that `getQoSObject()` method returns the most updated QoS information.
1. When playback switches bitrates, call the `BitrateChange` event in the Media Heartbeat instance.

   >[!IMPORTANT]
   >
   >Update the QoS object and call the bitrate change event on every bitrate change. This provides the most accurate QoS data.

The following sample code uses the JavaScript 2.x SDK for an HTML5 media player. You should use this code with the core media playback code.

```js
var mediaDelegate = new MediaHeartbeatDelegate();
...  

// This is called periodically by MediaHeartbeat instance
mediaDelegate.prototype.getQoSObject = function() {
    return this.qosInfo;
};

if (e.type == "qos_update") {
    var qosInfo = MediaHeartbeat.createQoSObject(<BITRATE>,<STARTUP_TIME>,<FPS>,<DROPPED_FRAMES>);
    mediaDelegate.qosInfo = qosInfo;
};

if (e.type == "bitrate_change") {
    this.mediaHeartbeat.trackEvent(MediaHeartbeat.Event.BitrateChange, qosObject);
};
```
