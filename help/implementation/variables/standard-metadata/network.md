---
title: Network
description: Set the broadcast network or channel name.
feature: Streaming Media
role: Developer
---

# Network

>[!BEGINSHADEBOX]

*This page covers data collection for the **Network** variable. See [Network](/help/reporting/variables/dimensions/network.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The network variable is the broadcast network or channel name (for example, `"Fox"`, `"ESPN"`, or `"HBO"`). Use it to compare engagement across networks within the same streaming property.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.network` |
| **XDM collection field** | [`mediaCollection.sessionDetails.network`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `network` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        network: "ESPN"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the network name as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.NETWORK`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.NETWORK] = "ESPN"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.NETWORK] = "ESPN"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `network` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "network": "ESPN"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `network` inside `mediaCollection.sessionDetails`:

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
          "channel": "Sports",
          "network": "ESPN"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the network in the `contextData` object using `ADB.Media.VideoMetadataKeys.Network`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.Network] = "ESPN";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.network` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.network": "ESPN"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
