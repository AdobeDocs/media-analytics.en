---
title: Stream type
description: Set the stream type to identify whether a media stream is audio or video content.
feature: Streaming Media
role: Developer
---

# Stream type

>[!BEGINSHADEBOX]

*This page covers data collection for the **Stream type** variable. See [Stream type](/help/reporting/variables/dimensions/core/stream-type.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The stream type variable identifies whether a media stream is audio or video content. It is required for all streaming media implementations and must be set at the start of every media session.

Setting stream type correctly is foundational to streaming media reporting. It enables the built-in **Media Stream Type** segments in Adobe Analytics (All media, Audio only, Video only) and drives separate audio and video reporting in Customer Journey Analytics. It also ensures that session data is correctly classified throughout the media analytics pipeline. Sessions with an unset or invalid stream type can be ungrouped or misclassified in downstream reporting.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.streamType` |
| **XDM collection field** | [`mediaCollection.sessionDetails.streamType`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Required** | Yes |
| **Sent with** | Session start, session close |

## Web SDK

Set `streamType` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        name: "video-123",
        friendlyName: "My Video",
        length: 128,
        contentType: "vod",
        playerName: "HTML5 Player",
        channel: "Sports",
        streamType: "video"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass `Media.MediaType.Video` or `Media.MediaType.Audio` as the `mediaType` argument to `createMediaObject`. Note that the `streamType` argument in `createMediaObject` controls the Content type variable (VOD, Live, etc.), not this variable.

**iOS (Swift)**

```swift
let mediaObject = Media.createMediaObjectWith(name: "video-123",
                                                id: "video-id",
                                            length: 128,
                                        streamType: MediaConstants.StreamType.VOD,
                                         mediaType: MediaType.Video)

tracker.trackSessionStart(info: mediaObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
var mediaInfo = Media.createMediaObject("video-123",
                                        "video-id",
                                        128,
                                        MediaConstants.StreamType.VOD,
                                        Media.MediaType.Video)

tracker.trackSessionStart(mediaInfo, null)
```

## Roku (BrightScript)

Set `streamType` inside `mediaCollection.sessionDetails` when calling `createMediaSession`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "name": "video-123",
                "friendlyName": "My Video",
                "length": 128,
                "contentType": "vod",
                "playerName": "Roku Player",
                "channel": "Sports",
                "streamType": "video"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `streamType` inside `mediaCollection.sessionDetails`:

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
          "streamType": "video"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass `ADB.Media.MediaType.Video` or `ADB.Media.MediaType.Audio` as the fifth argument to `Media.createMediaObject`:

```javascript
var mediaInfo = ADB.Media.createMediaObject(
  "My Video",               // name
  "video-123",              // media ID
  128,                      // length (seconds)
  ADB.Media.StreamType.VOD, // content type
  ADB.Media.MediaType.Video // stream type: Video or Audio
);

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.streamType` in the `params` object of your `sessionStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.streamType": "video"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure and all required fields.
