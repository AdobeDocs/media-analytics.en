---
title: Station
description: Set the radio station name or ID for audio broadcast content.
feature: Streaming Media
role: Developer
---

# Station

>[!BEGINSHADEBOX]

*This page covers data collection for the **Station** variable. See [Station](/help/reporting/dimensions/station.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The station variable is the name or ID of the radio station broadcasting the audio content (for example, `"NPR"` or `"WXYZ-FM"`). Use it to compare engagement across stations in a syndicated network.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.station` |
| **XDM collection field** | [`mediaCollection.sessionDetails.station`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.station` |
| **Required** | No |
| **Sent with** | [Session start](/help/implementation/events/session/session-start.md), session close |

## Web SDK

Set `station` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        station: "NPR"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the station as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.AudioMetadataKeys.STATION`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.AudioMetadataKeys.STATION] = "NPR"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.AudioMetadataKeys.STATION] = "NPR"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `station` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "station": "NPR"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `station` inside `mediaCollection.sessionDetails`:

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
          "station": "NPR"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the station in the `contextData` object using `ADB.Media.AudioMetadataKeys.Station`:

```javascript
var contextData = {};
contextData[ADB.Media.AudioMetadataKeys.Station] = "NPR";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.station` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.station": "NPR"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
