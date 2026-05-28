---
title: Bitrate change
description: Fire a bitrate change event whenever the player switches to a different bitrate.
feature: Streaming Media
role: Developer
---

# Bitrate change

>[!BEGINSHADEBOX]

*This page covers how to implement bitrate-change events. See [[!UICONTROL Bitrate changes] (dimension)](/help/reporting/dimensions/bitrate-changes.md) and [[!UICONTROL Bitrate changes] (metric)](/help/reporting/metrics/bitrate-changes.md) for the corresponding reporting variables.*

>[!ENDSHADEBOX]

The bitrate change event signals that the player has switched to a different bitrate. Update the [Bitrate](/help/implementation/variables/quality/bitrate.md) value on the QoE object first, then fire the bitrate change event. The backend uses the count of these events to compute the [[!UICONTROL Bitrate changes]](/help/reporting/dimensions/bitrate-changes.md) dimension and [[!UICONTROL Bitrate changes]](/help/reporting/metrics/bitrate-changes.md) metric, and the resulting bitrate values feed [[!UICONTROL Average bitrate]](/help/reporting/metrics/average-bitrate.md).

| Property | Value |
| --- | --- |
| **Context data variable** | (none — counted by the backend) |
| **XDM event type** | `media.bitrateChange` |
| **Audience Manager trait** | `c_contextdata.a.media.qoe.bitrateChangeCount` |
| **Required** | No |
| **Sent with** | [Bitrate change](/help/implementation/events/playback/bitrate-change.md) |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

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

>[!TAB iOS]

Update the QoE object with the new bitrate, then fire the bitrate change event.

```swift
let qoeObject = Media.createQoEObjectWith(bitrate: 4500,
                                       startupTime: 0,
                                               fps: 24,
                                     droppedFrames: 0)
tracker.updateQoEObject(qoe: qoeObject)
tracker.trackEvent(event: MediaEvent.BitrateChange, info: nil, metadata: nil)
```

>[!TAB Android]

Update the QoE object with the new bitrate, then fire the bitrate change event.

```kotlin
val qoeObject = Media.createQoEObject(4500L, 0.0, 24.0, 0L)
tracker.updateQoEObject(qoeObject)
tracker.trackEvent(Media.Event.BitrateChange, null, null)
```

>[!TAB Roku]

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

>[!TAB Media Edge API]

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

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Update the QoE object and fire the event:

```javascript
var qoeObject = ADB.Media.createQoEObject(4500, 0, 24, 0);
tracker.updateQoEObject(qoeObject);
tracker.trackEvent(ADB.Media.Event.BitrateChange);
```

>[!TAB Chromecast]

Update the QoS object with the new bitrate, then fire the bitrate change event:

```javascript
var qosInfo = ADBMobile.media.createQoSObject(
  4500,  // bitrate (kbps)
  0,     // startupTime
  24,    // fps
  0      // droppedFrames
);
ADBMobile.media.updateQoSObject(qosInfo);
ADBMobile.media.trackEvent(ADBMobile.media.Event.BitrateChange);
```

>[!TAB Media Collection API]

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

>[!ENDTABS]
