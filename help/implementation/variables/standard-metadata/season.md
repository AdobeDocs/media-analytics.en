---
title: Season
description: Set the season number for episodic content so engagement can be broken out by season.
feature: Streaming Media
role: Developer
---

# Season

>[!BEGINSHADEBOX]

*This page covers data collection for the **Season** variable. See [Season](/help/reporting/variables/dimensions/season.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The season variable is the season number for the show (typically a string integer like `"2"`). Set it for content that is part of a series so engagement can be broken out by season. Pair with [Show](/help/implementation/variables/standard-metadata/show.md) and [Episode](/help/implementation/variables/standard-metadata/episode.md) for full episodic context.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.season` |
| **XDM collection field** | [`mediaCollection.sessionDetails.season`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `season` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        season: "2"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the season as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.SEASON`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.SEASON] = "2"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.SEASON] = "2"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `season` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "season": "2"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `season` inside `mediaCollection.sessionDetails`:

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
          "season": "2"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the season in the `contextData` object using `ADB.Media.VideoMetadataKeys.Season`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.Season] = "2";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.season` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.season": "2"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
