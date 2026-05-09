---
title: Authorized
description: Flag a session as authenticated through Adobe Pass so it counts toward the Authorized event.
feature: Streaming Media
role: Developer
---

# Authorized

>[!BEGINSHADEBOX]

*This page covers data collection for the **Authorized** variable. See [Authorized](/help/reporting/variables/metrics/authorized.md) for the corresponding reporting metric.*

>[!ENDSHADEBOX]

The authorized variable flags a session whose user has been authorized through Adobe Pass / TV-Everywhere. Set it to `"TRUE"` when authorization is confirmed; leave it unset otherwise. Pair with [MVPD](/help/implementation/variables/standard-metadata/mvpd.md) to break out authentication by provider.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.pass.auth` |
| **XDM collection field** | [`mediaCollection.sessionDetails.authorized`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `authorized` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        authorized: "TRUE"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the authorized flag as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.AUTHORIZED`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.AUTHORIZED] = "TRUE"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.AUTHORIZED] = "TRUE"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `authorized` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "authorized": "TRUE"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `authorized` inside `mediaCollection.sessionDetails`:

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
          "authorized": "TRUE"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the authorized flag in the `contextData` object using `ADB.Media.VideoMetadataKeys.Authorized`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.Authorized] = "TRUE";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.pass.auth` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.pass.auth": "TRUE"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
