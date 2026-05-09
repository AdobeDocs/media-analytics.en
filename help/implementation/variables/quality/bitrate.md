---
title: Bitrate
description: Set the current playback bitrate (in kbps) on the QoE object so the backend can compute bitrate metrics.
feature: Streaming Media
role: Developer
---

# Bitrate

>[!BEGINSHADEBOX]

*This page covers data collection for the **Bitrate** variable. See [Average bitrate (dimension)](/help/reporting/variables/dimensions/average-bitrate.md) and [Average bitrate (metric)](/help/reporting/variables/metrics/average-bitrate.md) for the corresponding reporting variables.*

>[!ENDSHADEBOX]

The bitrate variable is the current playback bitrate, in kilobits per second. Set it on the QoE object whenever the player negotiates a bitrate, and update the QoE object when the bitrate changes. The backend uses bitrate values to compute Average bitrate, the per-bitrate-bucket dimension, and the Bitrate changes metric.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.qoe.bitrateAverageBucket` |
| **XDM collection field** | [`mediaCollection.qoeDataDetails.bitrate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-collection) |
| **Required** | No |
| **Sent with** | Quality events (bitrate change, buffer, error), session close |

## Web SDK

Set `bitrate` inside `mediaCollection.qoeDataDetails` on `media.bitrateChange` (or any quality-related event) when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

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

## Mobile SDK

Pass the bitrate as the first argument to `createQoEObject`. Update the QoE object on the tracker before any quality event fires.

**iOS (Swift)**

```swift
let qoeObject = Media.createQoEObjectWith(bitrate: 3200,
                                       startupTime: 0,
                                               fps: 24,
                                     droppedFrames: 0)

tracker.updateQoEObject(qoe: qoeObject)
```

**Android (Kotlin)**

```kotlin
val qoeObject = Media.createQoEObject(3200L,
                                      0.0,
                                      24.0,
                                      0L)

tracker.updateQoEObject(qoeObject)
```

## Roku (BrightScript)

Set `bitrate` inside `mediaCollection.qoeDataDetails` when calling `sendMediaEvent` for quality events such as `media.bitrateChange`:

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

## Media Edge API

Call the [bitrateChange](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bitratechange/#bitratechange) endpoint with `bitrate` inside `mediaCollection.qoeDataDetails`:

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

## Media SDK

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

## Media Collection API

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
