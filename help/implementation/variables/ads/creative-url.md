---
title: Creative URL
description: Set the URL of the ad creative for each ad.
feature: Streaming Media
role: Developer
---

# Creative URL

>[!BEGINSHADEBOX]

*This page covers data collection for the **Creative URL** variable. See [Creative URL](/help/reporting/variables/dimensions/creative-url.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The creative URL variable is the URL of the ad creative. Use the variable to track the asset location of each creative when the URL itself is meaningful for analysis (for example, distinguishing CDN paths or creative versions).

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.creativeURL` |
| **XDM collection field** | [`mediaCollection.advertisingDetails.creativeURL`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-collection) |
| **Required** | No |
| **Sent with** | Ad start, ad close |

## Web SDK

Set `creativeURL` inside `mediaCollection.advertisingDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adStart",
    mediaCollection: {
      advertisingDetails: {
        name: "ad-2125",
        creativeURL: "https://cdn.example.com/ads/creative-987.mp4"
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the creative URL as a metadata key in the HashMap argument to `trackEvent(AdStart)`. Use `MediaConstants.AdMetadataKeys.CREATIVE_URL`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.AdMetadataKeys.CREATIVE_URL] = "https://cdn.example.com/ads/creative-987.mp4"

tracker.trackEvent(event: MediaEvent.AdStart, info: adObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.AdMetadataKeys.CREATIVE_URL] = "https://cdn.example.com/ads/creative-987.mp4"

tracker.trackEvent(Media.Event.AdStart, adObject, metadata)
```

## Roku (BrightScript)

Set `creativeURL` inside `mediaCollection.advertisingDetails` when calling `sendMediaEvent` for `media.adStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adStart",
        "mediaCollection": {
            "advertisingDetails": {
                "name": "ad-2125",
                "creativeURL": "https://cdn.example.com/ads/creative-987.mp4"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [adStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adstart) endpoint with `creativeURL` inside `mediaCollection.advertisingDetails`:

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
          "podPosition": 0,
          "creativeURL": "https://cdn.example.com/ads/creative-987.mp4"
        },
        "sessionID": "{sid}",
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the creative URL in the `contextData` object using `ADB.Media.AdMetadataKeys.CreativeUrl`:

```javascript
var contextData = {};
contextData[ADB.Media.AdMetadataKeys.CreativeUrl] = "https://cdn.example.com/ads/creative-987.mp4";

tracker.trackEvent(ADB.Media.Event.AdStart, adInfo, contextData);
```

## Media Collection API

Include `media.ad.creativeURL` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adStart",
  "params": {
    "media.ad.creativeURL": "https://cdn.example.com/ads/creative-987.mp4"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
