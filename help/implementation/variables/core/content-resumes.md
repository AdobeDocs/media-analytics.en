---
title: Content resumes
description: Flag a session that resumes a previously interrupted playback so the backend counts a Content Resumes event.
feature: Streaming Media
role: Developer
---

# Content resumes

>[!BEGINSHADEBOX]

*This page covers data collection for the **Content resumes** variable. See [Content resumes](/help/reporting/metrics/content-resumes.md) for the corresponding reporting metric.*

>[!ENDSHADEBOX]

The content resumes variable flags a session that resumes a previously interrupted playback. Set it on `media.sessionStart` so that the backend counts a Content Resumes event for the session and excludes it from new-stream counts. For direct API and Edge API implementations, the client is responsible for detecting resumed sessions (for example, after a buffer, pause, or stall exceeding 30 minutes) and setting this flag accordingly.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.resume` |
| **XDM collection field** | [`mediaCollection.sessionDetails.hasResume`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | N/A |
| **Required** | No |
| **Sent with** | Session start |

## Web SDK

Set `hasResume` to `true` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) for the resumed session:

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
        streamType: "video",
        hasResume: true
      },
      playhead: 60
    }
  }
});
```

## Mobile SDK

Pass the resume flag as part of the media object's optional config bundle on `trackSessionStart`. Use the `MediaConstants.MediaObjectKey.RESUMED` key.

**iOS (Swift)**

```swift
var mediaObject = Media.createMediaObjectWith(name: "My Video",
                                                id: "video-123",
                                            length: 128,
                                        streamType: MediaConstants.StreamType.VOD,
                                         mediaType: MediaType.Video)
mediaObject?[MediaConstants.MediaObjectKey.RESUMED] = true

tracker.trackSessionStart(info: mediaObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val mediaInfo = Media.createMediaObject("My Video",
                                        "video-123",
                                        128,
                                        MediaConstants.StreamType.VOD,
                                        Media.MediaType.Video)
mediaInfo[MediaConstants.MediaObjectKey.RESUMED] = true

tracker.trackSessionStart(mediaInfo, null)
```

## Roku (BrightScript)

Set `hasResume` to `true` inside `mediaCollection.sessionDetails` when calling `createMediaSession` for the resumed session:

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
                "streamType": "video",
                "hasResume": true
            },
            "playhead": 60
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `hasResume` set to `true` inside `mediaCollection.sessionDetails`:

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
          "hasResume": true
        },
        "playhead": 60
      }
    }
  }]
}
```

## Media SDK

Set the `RESUMED` key on the media info object before calling `trackSessionStart`:

```javascript
var mediaInfo = ADB.Media.createMediaObject(
  "My Video",
  "video-123",
  128,
  ADB.Media.StreamType.VOD,
  ADB.Media.MediaType.Video
);
mediaInfo[ADB.Media.MediaObjectKey.Resumed] = true;

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.resume` in the `params` object of your `sessionStart` POST request:

```json
{
  "playerTime": { "playhead": 60, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.resume": true
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
