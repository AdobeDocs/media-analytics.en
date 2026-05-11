---
title: Ad length
description: Set the length of each ad in seconds.
feature: Streaming Media
role: Developer
---

# Ad length

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad length** variable. See [Ad length](/help/reporting/variables/dimensions/ad-length.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad length variable is the duration of the ad in seconds. Set it on every `media.adStart` event.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.length` |
| **XDM collection field** | [`mediaCollection.advertisingDetails.length`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-collection) |
| **Required** | Yes |
| **Sent with** | Ad start, ad close |

## Web SDK

Set `length` inside `mediaCollection.advertisingDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adStart",
    mediaCollection: {
      advertisingDetails: {
        name: "ad-2125",
        length: 15
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the ad length in seconds as the fourth argument to `createAdObject`.

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

Set `length` inside `mediaCollection.advertisingDetails` when calling `sendMediaEvent` for `media.adStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adStart",
        "mediaCollection": {
            "advertisingDetails": {
                "name": "ad-2125",
                "length": 15,
                "podPosition": 0,
                "playerName": "Roku Player"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [adStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adstart) endpoint with `length` inside `mediaCollection.advertisingDetails`:

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

Pass the ad length in seconds as the fourth argument to `ADB.Media.createAdObject`:

```javascript
var adInfo = ADB.Media.createAdObject(
  "Ford F-150",
  "ad-2125",
  0,
  15
);

tracker.trackEvent(ADB.Media.Event.AdStart, adInfo, contextData);
```

## Media Collection API

Include `media.ad.length` in the `params` object of your `adStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adStart",
  "params": {
    "media.ad.length": 15
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
