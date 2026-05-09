---
title: Ad ID
description: Set the unique identifier for each ad so that ad-level reporting and classifications join correctly.
feature: Streaming Media
role: Developer
---

# Ad ID

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad ID** variable. See [Ad](/help/reporting/variables/dimensions/ad.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad ID variable uniquely identifies each ad. It is required for every ad your player tracks. The value is the join key for the Ad reporting dimension and for ad-level classifications such as Creative ID, Pod name, and Pod position. Set it on every `media.adStart` event.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.name` |
| **XDM collection field** | [`mediaCollection.advertisingDetails.name`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-collection) |
| **Required** | Yes |
| **Sent with** | Ad start, ad close |

## Web SDK

Set `name` inside `mediaCollection.advertisingDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) for `media.adStart`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adStart",
    mediaCollection: {
      advertisingDetails: {
        name: "ad-2125",
        friendlyName: "Ford F-150",
        length: 15,
        playerName: "Freewheel",
        podPosition: 0
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the ad ID as the `adId` argument to `createAdObject`. The first argument (`name`) is the friendly name; the second is the ID.

**iOS (Swift)**

```swift
let adObject = Media.createAdObjectWith(name: "Ford F-150",
                                          id: "ad-2125",
                                    position: 0,
                                      length: 15)

tracker.trackEvent(event: MediaEvent.AdStart, info: adObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val adObject = Media.createAdObject("Ford F-150",
                                    "ad-2125",
                                    0L,
                                    15.0)

tracker.trackEvent(Media.Event.AdStart, adObject, null)
```

## Roku (BrightScript)

Set `name` inside `mediaCollection.advertisingDetails` when calling `sendMediaEvent` for `media.adStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adStart",
        "mediaCollection": {
            "advertisingDetails": {
                "name": "ad-2125",
                "friendlyName": "Ford F-150",
                "length": 15,
                "playerName": "Roku Player",
                "podPosition": 0
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [adStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adstart) endpoint with `name` inside `mediaCollection.advertisingDetails`:

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

Pass the ad ID as the second argument to `ADB.Media.createAdObject`:

```javascript
var adInfo = ADB.Media.createAdObject(
  "Ford F-150",   // name (friendly name)
  "ad-2125",      // ad ID
  0,              // position in pod
  15              // length (seconds)
);

tracker.trackEvent(ADB.Media.Event.AdStart, adInfo, contextData);
```

## Media Collection API

Include `media.ad.id` in the `params` object of your `adStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adStart",
  "params": {
    "media.ad.id": "ad-2125"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
