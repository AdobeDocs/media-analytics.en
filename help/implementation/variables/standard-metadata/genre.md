---
title: Genre
description: Set the content genre as a comma-delimited string. Multi-genre content splits across line items in reporting.
feature: Streaming Media
role: Developer
---

# Genre

>[!BEGINSHADEBOX]

*This page covers data collection for the **Genre** variable. See [Genre](/help/reporting/dimensions/genre.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The genre variable is the content genre as defined by the producer (for example, `"Drama"`, `"Comedy"`, or `"Drama,Action"`). Comma-delimit multiple values when the content fits more than one genre. In reporting, the list variable splits each value into a separate line item, with each line item receiving equal metric weight.

>[!NOTE]
>
>In the reporting pipeline, the genre value is exposed as `mediaReporting.sessionDetails.genreList` (a list field). The older `mediaReporting.sessionDetails.genre` path remains functional but `genreList` is recommended.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.genre` |
| **XDM collection field** | [`mediaCollection.sessionDetails.genre`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `genre` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        genre: "Drama,Action"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the genre string as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.GENRE`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.GENRE] = "Drama,Action"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.GENRE] = "Drama,Action"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `genre` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "genre": "Drama,Action"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `genre` inside `mediaCollection.sessionDetails`:

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
          "genre": "Drama,Action"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the genre in the `contextData` object using `ADB.Media.VideoMetadataKeys.Genre`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.Genre] = "Drama,Action";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.genre` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.genre": "Drama,Action"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
