---
title: Asset ID
description: Set the asset ID, a stable industry identifier for the media asset such as an EIDR or TMS/Gracenote ID.
feature: Streaming Media
role: Developer
---

# Asset ID

>[!BEGINSHADEBOX]

*This page covers data collection for the **Asset ID** variable. See [Asset ID](/help/reporting/dimensions/asset-id.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The asset ID variable is the unique identifier for the underlying media asset (for example, an episode ID, a movie ID, or a live event ID). Typically sourced from metadata authorities such as EIDR, TMS/Gracenote, or Rovi, but proprietary or in-house IDs are also accepted. Use it when you need to compare engagement across distribution platforms that may assign different content IDs to the same underlying asset.

>[!NOTE]
>
>The XDM collection field uses uppercase `ID`: `assetID`.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.asset` |
| **XDM collection field** | [`mediaCollection.sessionDetails.assetID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.asset` |
| **Required** | No |
| **Sent with** | Session start, session close |

## Web SDK

Set `assetID` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        assetID: "89745363"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the asset ID as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.ASSET_ID`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.ASSET_ID] = "89745363"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.ASSET_ID] = "89745363"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `assetID` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "assetID": "89745363"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `assetID` inside `mediaCollection.sessionDetails`:

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
          "assetID": "89745363"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the asset ID in the `contextData` object using `ADB.Media.VideoMetadataKeys.AssetId`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.AssetId] = "89745363";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.assetId` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.assetId": "89745363"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
