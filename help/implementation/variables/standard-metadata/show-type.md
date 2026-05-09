---
title: Show type
description: Identify the content format (full episode, preview, clip, or other) using a string integer code.
feature: Streaming Media
role: Developer
---

# Show type

>[!BEGINSHADEBOX]

*This page covers data collection for the **Show type** variable. See [Show type](/help/reporting/variables/dimensions/show-type.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The show type variable identifies the content format using a string integer code:

- `"0"`: Full episode
- `"1"`: Preview or trailer
- `"2"`: Clip
- `"3"`: Other

Use it to separate full-program viewing from short-form content like trailers and clips when measuring engagement.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.type` |
| **XDM collection field** | [`mediaCollection.sessionDetails.showType`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `showType` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        showType: "0"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the show type as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.SHOW_TYPE`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.SHOW_TYPE] = "0"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.SHOW_TYPE] = "0"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `showType` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "showType": "0"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `showType` inside `mediaCollection.sessionDetails`:

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
          "showType": "0"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the show type in the `contextData` object using `ADB.Media.VideoMetadataKeys.ShowType`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.ShowType] = "0";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.showType` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.showType": "0"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
