---
title: Ad player name
description: Set the name of the player that renders ads. The ad player can differ from the main content player.
feature: Streaming Media
role: Developer
---

# Ad player name

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad player name** variable. See [Ad player name](/help/reporting/variables/dimensions/ad-player-name.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad player name variable identifies which player rendered each ad (for example, `"Freewheel"`, `"Google IMA"`). The ad player can differ from the main content player when ads are stitched in by a server-side ad insertion service. Use this variable to compare quality and completion across ad-serving stacks.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.playerName` |
| **XDM collection field** | [`mediaCollection.advertisingDetails.playerName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-collection) |
| **Required** | Yes |
| **Sent with** | Ad start, ad close |

## Web SDK

Set `playerName` inside `mediaCollection.advertisingDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adStart",
    mediaCollection: {
      advertisingDetails: {
        name: "ad-2125",
        playerName: "Freewheel"
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the ad player name as the `MediaConstants.AdMetadataKeys.AD_PLAYER` key in the metadata HashMap argument to `trackEvent(AdStart)`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.AdMetadataKeys.AD_PLAYER] = "Freewheel"

tracker.trackEvent(event: MediaEvent.AdStart, info: adObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.AdMetadataKeys.AD_PLAYER] = "Freewheel"

tracker.trackEvent(Media.Event.AdStart, adObject, metadata)
```

## Roku (BrightScript)

Set `playerName` inside `mediaCollection.advertisingDetails` when calling `sendMediaEvent` for `media.adStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adStart",
        "mediaCollection": {
            "advertisingDetails": {
                "name": "ad-2125",
                "playerName": "Freewheel",
                "length": 15,
                "podPosition": 0
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [adStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adstart) endpoint with `playerName` inside `mediaCollection.advertisingDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.adStart",
      "mediaCollection": {
        "advertisingDetails": {
          "name": "ad-2125",
          "length": 15,
          "playerName": "Freewheel",
          "podPosition": 0
        },
        "sessionID": "{sid}",
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the ad player name in the `contextData` object using `ADB.Media.AdMetadataKeys.AdPlayer`:

```javascript
var contextData = {};
contextData[ADB.Media.AdMetadataKeys.AdPlayer] = "Freewheel";

tracker.trackEvent(ADB.Media.Event.AdStart, adInfo, contextData);
```

## Media Collection API

Include `media.ad.playerName` in the `params` object of your `adStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adStart",
  "params": {
    "media.ad.playerName": "Freewheel"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
