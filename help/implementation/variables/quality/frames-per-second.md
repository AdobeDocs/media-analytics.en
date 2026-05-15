---
title: Frames per second
description: Set the current frame rate on the QoE object so the backend has frame-rate context for quality reporting.
feature: Streaming Media
role: Developer
---

# Frames per second

The frames per second variable is the current frame rate of the stream. Set it on the QoE object alongside bitrate and dropped frames so the backend has full quality context for each playback session. Adobe Analytics does not auto-create a reporting variable for frame rate; create a custom processing rule if you want it surfaced as a report.

| Property | Value |
| --- | --- |
| **Context data variable** | None (Adobe Analytics does not assign a reserved context data key for frame rate) |
| **XDM collection field** | [`mediaCollection.qoeDataDetails.framesPerSecond`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-collection) |
| **Audience Manager trait** | N/A |
| **Required** | No |
| **Sent with** | Quality events ([bitrate change](/help/implementation/events/playback/bitrate-change.md), [buffer start](/help/implementation/events/playback/buffer-start.md), [error](/help/implementation/events/error.md)), session close |

## Web SDK

Set `framesPerSecond` inside `mediaCollection.qoeDataDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.bitrateChange",
    mediaCollection: {
      qoeDataDetails: {
        bitrate: 3200,
        framesPerSecond: 24
      },
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

## Mobile SDK

Pass the frame rate as the third argument (`fps`) to `createQoEObject`.

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

Set `framesPerSecond` inside `mediaCollection.qoeDataDetails` when calling `sendMediaEvent`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.bitrateChange",
        "mediaCollection": {
            "qoeDataDetails": {
                "bitrate": 3200,
                "framesPerSecond": 24
            },
            "playhead": 90
        }
    }
})
```

## Media Edge API

Call the [bitrateChange](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bitratechange/#bitratechange) endpoint with `framesPerSecond` inside `mediaCollection.qoeDataDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.bitrateChange",
      "mediaCollection": {
        "qoeDataDetails": {
          "framesPerSecond": 24
        },
        "sessionID": "{sid}",
        "playhead": 90
      }
    }
  }]
}
```

## Media SDK

Pass the frame rate as the third argument to `ADB.Media.createQoEObject`:

```javascript
var qoeObject = ADB.Media.createQoEObject(3200, 0, 24, 0);
tracker.updateQoEObject(qoeObject);
```

## Media Collection API

Include `media.qoe.framesPerSecond` in the `params` object:

```json
{
  "playerTime": { "playhead": 90, "ts": 1699523820000 },
  "eventType": "bitrateChange",
  "params": {
    "media.qoe.framesPerSecond": 24
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
