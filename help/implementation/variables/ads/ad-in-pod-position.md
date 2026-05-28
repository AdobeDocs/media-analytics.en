---
title: Ad in pod position
description: Set the index position of the ad inside its parent ad break. The first ad has index 0.
feature: Streaming Media
role: Developer
---

# Ad in pod position

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad in pod position** variable. See [Ad in pod position](/help/reporting/dimensions/ad-in-pod-position.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad in pod position variable is the zero-indexed position of the ad inside its parent ad break. The first ad in a pod has index `0`, the second has index `1`, and so on. Use the dimension to compare engagement and completion by position within an ad break.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.podPosition` |
| **XDM collection field** | [`xdm.mediaCollection.advertisingDetails.podPosition`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.ad.podPosition` |
| **Required** | Yes |
| **Sent with** | [Ad start](/help/implementation/events/ads/ad-start.md), ad close |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `podPosition` inside `xdm.mediaCollection.advertisingDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adStart",
    mediaCollection: {
      advertisingDetails: {
        name: "ad-2125",
        podPosition: 0
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

>[!TAB iOS]

Pass the position as the third argument to `createAdObject`.

```swift
let adObject = Media.createAdObjectWith(name: "Ford F-150",
                                          id: "ad-2125",
                                    position: 0,
                                      length: 15)

tracker.trackEvent(event: MediaEvent.AdStart, info: adObject, metadata: nil)
```

>[!TAB Android]

Pass the position as the third argument to `createAdObject`.

```kotlin
val adObject = Media.createAdObject("Ford F-150",
                                    "ad-2125",
                                    0L,
                                    15.0)

tracker.trackEvent(Media.Event.AdStart, adObject, null)
```

>[!TAB Roku]

Set `podPosition` inside `xdm.mediaCollection.advertisingDetails` when calling `sendMediaEvent` for `media.adStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adStart",
        "mediaCollection": {
            "advertisingDetails": {
                "name": "ad-2125",
                "podPosition": 0,
                "length": 15,
                "playerName": "Roku Player"
            },
            "playhead": 0
        }
    }
})
```

>[!TAB Media Edge API]

Call the [adStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adstart) endpoint with `podPosition` inside `xdm.mediaCollection.advertisingDetails`:

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

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Pass the position as the third argument to `ADB.Media.createAdObject`:

```javascript
var adInfo = ADB.Media.createAdObject(
  "Ford F-150",
  "ad-2125",
  0,
  15
);

tracker.trackEvent(ADB.Media.Event.AdStart, adInfo, contextData);
```

>[!TAB Chromecast]

Pass the position as the third argument to `ADBMobile.media.createAdObject`:

```javascript
var adInfo = ADBMobile.media.createAdObject(
  "Ford F-150",
  "ad-2125",
  1,
  30
);
ADBMobile.media.trackEvent(ADBMobile.media.Event.AdStart, adInfo, null);
```

>[!TAB Media Collection API]

Include `media.ad.podPosition` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adStart",
  "params": {
    "media.ad.podPosition": 0
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
