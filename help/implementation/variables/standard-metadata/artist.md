---
title: Artist
description: Set the performing artist name for audio content.
feature: Streaming Media
role: Developer
---

# Artist

>[!BEGINSHADEBOX]

*This page covers data collection for the **Artist** variable. See [Artist](/help/reporting/dimensions/artist.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The artist variable is the name of the performing artist for audio content (for example, `"Crested Larks"`). Use it on music or podcast sessions to break engagement out by performer.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.artist` |
| **XDM collection field** | [`mediaCollection.sessionDetails.artist`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.artist` |
| **Required** | No |
| **Sent with** | [Session start](/help/implementation/events/session/session-start.md), session close |

## Web SDK

Set `artist` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        artist: "Crested Larks"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the artist name as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.AudioMetadataKeys.ARTIST`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.AudioMetadataKeys.ARTIST] = "Crested Larks"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.AudioMetadataKeys.ARTIST] = "Crested Larks"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `artist` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "artist": "Crested Larks"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `artist` inside `mediaCollection.sessionDetails`:

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
          "artist": "Crested Larks"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the artist in the `contextData` object using `ADB.Media.AudioMetadataKeys.Artist`:

```javascript
var contextData = {};
contextData[ADB.Media.AudioMetadataKeys.Artist] = "Crested Larks";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.artist` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.artist": "Crested Larks"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
