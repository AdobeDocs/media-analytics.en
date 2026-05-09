---
title: Bitrate change
description: Fire a bitrate change event whenever the player switches to a different bitrate.
feature: Streaming Media
role: Developer
---

# Bitrate change

>[!BEGINSHADEBOX]

*This page covers how to implement bitrate-change events. See [Bitrate changes (dimension)](/help/reporting/variables/dimensions/bitrate-changes.md) and [Bitrate changes (metric)](/help/reporting/variables/metrics/bitrate-changes.md) for the corresponding reporting variables.*

>[!ENDSHADEBOX]

The bitrate change event signals that the player has switched to a different bitrate. Update the [Bitrate](/help/implementation/variables/quality/bitrate.md) value on the QoE object first, then fire the bitrate change event. The backend uses the count of these events to compute the Bitrate changes dimension and metric, and the resulting bitrate values feed Average bitrate.

| Property | Value |
| --- | --- |
| **Context data variable** | (none — counted by the backend) |
| **XDM event type** | `media.bitrateChange` |
| **Required** | No |
| **Sent with** | Whenever the player switches bitrate |

## Web SDK

Use [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) to send a `media.bitrateChange` event with the new bitrate:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.bitrateChange",
    mediaCollection: {
      qoeDataDetails: {
        bitrate: 4500,
        droppedFrames: 0,
        framesPerSecond: 24,
        timeToStart: 0
      },
      sessionID: "{sid}",
      playhead: 120
    }
  }
});
```

## Mobile SDK

Update the QoE object with the new bitrate, then fire the bitrate change event.

**iOS (Swift)**

```swift
let qoeObject = Media.createQoEObjectWith(bitrate: 4500,
                                       startupTime: 0,
                                               fps: 24,
                                     droppedFrames: 0)
tracker.updateQoEObject(qoe: qoeObject)
tracker.trackEvent(event: MediaEvent.BitrateChange, info: nil, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val qoeObject = Media.createQoEObject(4500L, 0.0, 24.0, 0L)
tracker.updateQoEObject(qoeObject)
tracker.trackEvent(Media.Event.BitrateChange, null, null)
```

## Roku (BrightScript)

Use `sendMediaEvent` with `media.bitrateChange` to signal a bitrate change. Include the new bitrate in `qoeDataDetails`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.bitrateChange",
        "mediaCollection": {
            "qoeDataDetails": {
                "bitrate": 4500,
                "droppedFrames": 0,
                "framesPerSecond": 24,
                "timeToStart": 0
            },
            "playhead": 120
        }
    }
})
```

## Media Edge API

Call the [bitrateChange](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bitratechange/#bitratechange) endpoint with the updated `qoeDataDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.bitrateChange",
      "mediaCollection": {
        "qoeDataDetails": {
          "bitrate": 4500
        },
        "sessionID": "{sid}",
        "playhead": 120
      }
    }
  }]
}
```

## Media SDK

Update the QoE object and fire the event:

```javascript
var qoeObject = ADB.Media.createQoEObject(4500, 0, 24, 0);
tracker.updateQoEObject(qoeObject);
tracker.trackEvent(ADB.Media.Event.BitrateChange);
```

## Media Collection API

Send a `bitrateChange` POST request with the new bitrate:

```json
{
  "playerTime": { "playhead": 120, "ts": 1699523820000 },
  "eventType": "bitrateChange",
  "params": {
    "media.qoe.bitrate": 4500
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
