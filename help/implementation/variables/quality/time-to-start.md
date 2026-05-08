---
title: Time to start
description: Set the startup time of the player, in milliseconds, so the backend can report time-to-first-frame quality.
feature: Streaming Media
role: Developer
---

# Time to start

>[!BEGINSHADEBOX]

*This page covers data collection for the **Time to start** variable. See [Time to start](/help/reporting/variables/dimensions/quality/time-to-start.md) for the corresponding reporting dimension and metric.*

>[!ENDSHADEBOX]

The time to start variable is the elapsed time, in milliseconds, between the player initiating playback and the first frame rendering. Set it on the QoE object before the session start event fires. Adobe stores and reports the value in seconds; pass milliseconds and Adobe converts at ingest.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.qoe.timeToStart` |
| **XDM collection field** | [`mediaCollection.qoeDataDetails.timeToStart`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-collection) |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `timeToStart` inside `mediaCollection.qoeDataDetails` on `media.sessionStart` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        name: "video-123",
        length: 128,
        contentType: "vod",
        playerName: "HTML5 Player",
        channel: "Sports",
        streamType: "video"
      },
      qoeDataDetails: {
        timeToStart: 30000
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass startup time as the second argument (`startupTime`) to `createQoEObject`.

**iOS (Swift)**

```swift
let qoeObject = Media.createQoEObjectWith(bitrate: 3200,
                                       startupTime: 30000,
                                               fps: 24,
                                     droppedFrames: 0)

tracker.updateQoEObject(qoe: qoeObject)
```

**Android (Kotlin)**

```kotlin
val qoeObject = Media.createQoEObject(3200L,
                                      30000.0,
                                      24.0,
                                      0L)

tracker.updateQoEObject(qoeObject)
```

## Roku (BrightScript)

Set `timeToStart` inside `mediaCollection.qoeDataDetails` on `media.sessionStart` when calling `createMediaSession`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "name": "video-123",
                "length": 128,
                "contentType": "vod",
                "playerName": "Roku Player",
                "channel": "Sports",
                "streamType": "video"
            },
            "qoeDataDetails": {
                "timeToStart": 30000
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `timeToStart` inside `mediaCollection.qoeDataDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.sessionStart",
      "mediaCollection": {
        "sessionDetails": {
          "name": "video-123",
          "length": 128,
          "contentType": "vod",
          "playerName": "HTML5 Player",
          "channel": "Sports"
        },
        "qoeDataDetails": {
          "timeToStart": 30000
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass time to start as the second argument to `ADB.Media.createQoEObject`:

```javascript
var qoeObject = ADB.Media.createQoEObject(3200, 30000, 24, 0);
tracker.updateQoEObject(qoeObject);
```

## Media Collection API

Include `media.qoe.timeToStart` in the `params` object on `sessionStart`:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.qoe.timeToStart": 30000
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
