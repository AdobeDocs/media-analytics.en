---
title: Content type
description: Set the content type to identify the format of the stream (VOD, Live, Linear, podcast, song, and so on).
feature: Streaming Media
role: Developer
---

# Content type

>[!BEGINSHADEBOX]

*This page covers data collection for the **Content type** variable. See [Content type](/help/reporting/dimensions/content-type.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The content type variable identifies the format of the stream (for example, VOD, Live, or Linear for video, or podcast or audiobook for audio). It is required for all streaming media implementations and must be set at session start. Adobe-defined values populate the built-in Content Type segments and reports; custom strings are also accepted but will not match the built-in segments. If unset, the value defaults to `missing_content_type`.

Recommended values:

* **Video:** `vod`, `live`, `linear`, `ugc`, `dvod`
* **Audio:** `song`, `podcast`, `audiobook`, `radio`

| Property | Value |
| --- | --- |
| **Context data variable** | `a.contentType` |
| **XDM collection field** | [`mediaCollection.sessionDetails.contentType`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.contentType` |
| **Required** | Yes |
| **Sent with** | [Session start](/help/implementation/events/session/session-start.md), session close |

## Web SDK

Set `contentType` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

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
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the content type constant as the `streamType` argument to `createMediaObject`. Use `MediaConstants.StreamType.*` values such as `VOD`, `LIVE`, `LINEAR`, `AOD`, `PODCAST`. Note: in the Mobile SDK, the `streamType` argument controls Content Type. The Stream Type variable (audio vs. video) is the separate `mediaType` argument.

**iOS (Swift)**

```swift
let mediaObject = Media.createMediaObjectWith(name: "My Video",
                                                id: "video-123",
                                            length: 128,
                                        streamType: MediaConstants.StreamType.VOD,
                                         mediaType: MediaType.Video)

tracker.trackSessionStart(info: mediaObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
var mediaInfo = Media.createMediaObject("My Video",
                                        "video-123",
                                        128,
                                        MediaConstants.StreamType.VOD,
                                        Media.MediaType.Video)

tracker.trackSessionStart(mediaInfo, null)
```

## Roku (BrightScript)

Set `contentType` inside `mediaCollection.sessionDetails` when calling `createMediaSession`:

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
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `contentType` inside `mediaCollection.sessionDetails`:

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
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass an `ADB.Media.StreamType.*` constant as the fourth argument to `ADB.Media.createMediaObject`:

```javascript
var mediaInfo = ADB.Media.createMediaObject(
  "My Video",
  "video-123",
  128,
  ADB.Media.StreamType.VOD, // Content type — VOD, LIVE, LINEAR, etc.
  ADB.Media.MediaType.Video
);

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.contentType` in the `params` object of your `sessionStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.contentType": "vod"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
