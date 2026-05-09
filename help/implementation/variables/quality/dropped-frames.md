---
title: Dropped frames
description: Set the running count of dropped frames on the QoE object so the backend can report frame-drop quality.
feature: Streaming Media
role: Developer
---

# Dropped frames

>[!BEGINSHADEBOX]

*This page covers data collection for the **Dropped frames** variable. See [Dropped frames](/help/reporting/variables/dimensions/dropped-frames.md) for the corresponding reporting dimension and metric.*

>[!ENDSHADEBOX]

The dropped frames variable is the running count of frames the player has dropped during the session. Set it on the QoE object and update the value whenever the player reports new drops. The backend reports the latest value at session close.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.qoe.droppedFrameCount` |
| **XDM collection field** | [`mediaCollection.qoeDataDetails.droppedFrames`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-collection) |
| **Required** | No |
| **Sent with** | Quality events, session close |

## Web SDK

Set `droppedFrames` inside `mediaCollection.qoeDataDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.bitrateChange",
    mediaCollection: {
      qoeDataDetails: {
        bitrate: 3200,
        droppedFrames: 3
      },
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

## Mobile SDK

Pass dropped frames as the fourth argument to `createQoEObject`. Update the tracker before any quality event fires.

**iOS (Swift)**

```swift
let qoeObject = Media.createQoEObjectWith(bitrate: 3200,
                                       startupTime: 0,
                                               fps: 24,
                                     droppedFrames: 3)

tracker.updateQoEObject(qoe: qoeObject)
```

**Android (Kotlin)**

```kotlin
val qoeObject = Media.createQoEObject(3200L,
                                      0.0,
                                      24.0,
                                      3L)

tracker.updateQoEObject(qoeObject)
```

## Roku (BrightScript)

Set `droppedFrames` inside `mediaCollection.qoeDataDetails` when calling `sendMediaEvent`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.bitrateChange",
        "mediaCollection": {
            "qoeDataDetails": {
                "bitrate": 3200,
                "droppedFrames": 3
            },
            "playhead": 90
        }
    }
})
```

## Media Edge API

Call the [bitrateChange](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bitratechange/#bitratechange) endpoint with `droppedFrames` inside `mediaCollection.qoeDataDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.bitrateChange",
      "mediaCollection": {
        "qoeDataDetails": {
          "droppedFrames": 3
        },
        "sessionID": "{sid}",
        "playhead": 90
      }
    }
  }]
}
```

## Media SDK

Pass dropped frames as the fourth argument to `ADB.Media.createQoEObject`:

```javascript
var qoeObject = ADB.Media.createQoEObject(3200, 0, 24, 3);
tracker.updateQoEObject(qoeObject);
```

## Media Collection API

Include `media.qoe.droppedFrames` in the `params` object:

```json
{
  "playerTime": { "playhead": 90, "ts": 1699523820000 },
  "eventType": "bitrateChange",
  "params": {
    "media.qoe.droppedFrames": 3
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
