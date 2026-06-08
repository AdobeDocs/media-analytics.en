---
title: Bitrate
description: Set the current playback bitrate (in kbps) on the QoE object so the backend can compute bitrate metrics.
feature: Streaming Media
role: Developer
---

# Bitrate

>[!BEGINSHADEBOX]

*This page covers data collection for the **Bitrate** variable. See [[!UICONTROL Average bitrate] (dimension)](/help/reporting/dimensions/average-bitrate.md) and [[!UICONTROL Average bitrate] (metric)](/help/reporting/metrics/average-bitrate.md) for the corresponding reporting variables.*

>[!ENDSHADEBOX]

The bitrate variable is the current playback bitrate, in kilobits per second. Set it on the QoE object whenever the player negotiates a bitrate, and update the QoE object when the bitrate changes. The backend uses bitrate values to compute [[!UICONTROL Average bitrate]](/help/reporting/metrics/average-bitrate.md), the per-bitrate-bucket dimension, and the [[!UICONTROL Bitrate changes]](/help/reporting/metrics/bitrate-changes.md) metric.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.qoe.bitrateAverageBucket` |
| **XDM collection field** | [`xdm.mediaCollection.qoeDataDetails.bitrate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.qoe.bitrateAverageBucket` |
| **Required** | No |
| **Sent with** | Quality events ([bitrate change](/help/implementation/events/playback/bitrate-change.md), [buffer start](/help/implementation/events/playback/buffer-start.md), [error](/help/implementation/events/error.md)), session close |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `bitrate` inside `xdm.mediaCollection.qoeDataDetails` on `media.bitrateChange` (or any quality-related event) when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.bitrateChange",
    mediaCollection: {
      qoeDataDetails: {
        bitrate: 3200,
        droppedFrames: 0,
        framesPerSecond: 24,
        timeToStart: 0
      },
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

>[!TAB iOS]

Pass the bitrate as the first argument to `createQoEObject`. Update the QoE object on the tracker before any quality event fires.

```swift
let qoeObject = Media.createQoEObjectWith(bitrate: 3200,
                                       startupTime: 0,
                                               fps: 24,
                                     droppedFrames: 0)

tracker.updateQoEObject(qoe: qoeObject)
```

>[!TAB Android]

Pass the bitrate as the first argument to `createQoEObject`. Update the QoE object on the tracker before any quality event fires.

```kotlin
val qoeObject = Media.createQoEObject(3200L,
                                      0.0,
                                      24.0,
                                      0L)

tracker.updateQoEObject(qoeObject)
```

>[!TAB Roku Edge]

Set `bitrate` inside `xdm.mediaCollection.qoeDataDetails` when calling `sendMediaEvent` for quality events such as `media.bitrateChange`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.bitrateChange",
        "mediaCollection": {
            "qoeDataDetails": {
                "bitrate": 3200,
                "droppedFrames": 0,
                "framesPerSecond": 24,
                "timeToStart": 0
            },
            "playhead": 90
        }
    }
})
```

>[!TAB Media Edge API]

Call the [bitrateChange](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bitratechange/#bitratechange) endpoint with `bitrate` inside `xdm.mediaCollection.qoeDataDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.bitrateChange",
      "mediaCollection": {
        "qoeDataDetails": {
          "bitrate": 3200
        },
        "sessionID": "{sid}",
        "playhead": 90
      }
    }
  }]
}
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Pass the bitrate as the first argument to `ADB.Media.createQoEObject` and update the tracker:

```javascript
var qoeObject = ADB.Media.createQoEObject(
  3200,  // bitrate (kbps)
  0,     // startup time (ms)
  24,    // fps
  0      // dropped frames
);

tracker.updateQoEObject(qoeObject);
```

>[!TAB Chromecast]

Pass the bitrate in kbps as the first argument to `ADBMobile.media.createQoSObject` and update the tracker:

```javascript
var qosInfo = ADBMobile.media.createQoSObject(
  3200,  // bitrate (kbps)
  0,     // startupTime
  24,    // fps
  0      // droppedFrames
);
ADBMobile.media.updateQoSObject(qosInfo);
```

>[!TAB Roku 2.x]

Pass the bitrate in kbps as the first argument to `adb_media_init_qosinfo` and update the tracker with `mediaUpdateQoS`:

```brightscript
adb = ADBMobile()
qosInfo = adb_media_init_qosinfo(3200.0, 0.0, 24.0, 0.0)  ' bitrate, startupTime, fps, droppedFrames

adb.mediaUpdateQoS(qosInfo)
```

>[!TAB Media Collection API]

Include `media.qoe.bitrate` in the `params` object of your `bitrateChange` POST request:

```json
{
  "playerTime": { "playhead": 90, "ts": 1699523820000 },
  "eventType": "bitrateChange",
  "params": {
    "media.qoe.bitrate": 3200
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
