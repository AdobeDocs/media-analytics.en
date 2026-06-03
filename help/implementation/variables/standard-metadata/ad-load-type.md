---
title: Ad load type
description: Set the type of ad load for the streaming session.
feature: Streaming Media
role: Developer
---

# Ad load type

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad load type** variable. See [Ad loads](/help/reporting/dimensions/ad-load-type.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad load type variable identifies the type of ad loaded at the start of the session. This value is defined by your organization's internal ad delivery system and is not constrained to a standard enumeration. You can use any string meaningful to your implementation, such as `"linear"`, `"dynamic"`, or `"programmatic"`.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.adLoad` |
| **XDM collection field** | [`xdm.mediaCollection.sessionDetails.adLoad`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.adLoad` |
| **Required** | No |
| **Sent with** | [Session start](/help/implementation/events/session/session-start.md), session close |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `adLoad` inside `xdm.mediaCollection.sessionDetails` when calling [`createMediaSession`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/createmediasession):

```javascript
alloy("createMediaSession", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        name: "video-123",
        friendlyName: "My Video",
        length: 300,
        contentType: "vod",
        playerName: "HTML5 Player",
        channel: "Sports",
        adLoad: "linear"
      },
      playhead: 0
    }
  }
});
```

>[!TAB iOS]

Pass the ad load type as a metadata key in the dictionary argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.AD_LOAD`.

```swift
var videoMetadata: [String: String] = [:]
videoMetadata[MediaConstants.VideoMetadataKeys.AD_LOAD] = "linear"

tracker.trackSessionStart(info: mediaObject, metadata: videoMetadata)
```

>[!TAB Android]

Pass the ad load type as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.AD_LOAD`.

```kotlin
val videoMetadata = HashMap<String, String>()
videoMetadata[MediaConstants.VideoMetadataKeys.AD_LOAD] = "linear"

tracker.trackSessionStart(mediaInfo, videoMetadata)
```

>[!TAB Roku]

Use `createMediaSession` to set `adLoad` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "adLoad": "linear"
            },
            "playhead": 0
        }
    }
})
```

>[!TAB Media Edge API]

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `adLoad` inside `xdm.mediaCollection.sessionDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.sessionStart",
      "mediaCollection": {
        "sessionDetails": {
          "name": "video-123",
          "length": 300,
          "contentType": "vod",
          "playerName": "HTML5 Player",
          "channel": "Sports",
          "adLoad": "linear"
        },
        "playhead": 0
      }
    }
  }]
}
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Pass the ad load type in the `contextData` object using `ADB.Media.VideoMetadataKeys.AdLoad`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.AdLoad] = "linear";

tracker.trackSessionStart(mediaInfo, contextData);
```

>[!TAB Chromecast]

Use `ADBMobile.media.VideoMetadataKeys.AD_LOAD` to set the ad load type in the `StandardMediaMetadata` property of the media object before calling `trackSessionStart`:

```javascript
var mediaInfo = ADBMobile.media.createMediaObject("My Video", "video-123", 300,
  ADBMobile.media.StreamType.VOD, ADBMobile.media.MediaType.Video);
var standardMetadata = {};
standardMetadata[ADBMobile.media.VideoMetadataKeys.AD_LOAD] = "linear";
mediaInfo[ADBMobile.media.MediaObjectKey.StandardMediaMetadata] = standardMetadata;
ADBMobile.media.trackSessionStart(mediaInfo, null);
```

>[!TAB Media Collection API]

Include `media.adLoad` in the `params` object of your `sessionStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.adLoad": "linear"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.

>[!ENDTABS]
