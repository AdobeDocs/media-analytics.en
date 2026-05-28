---
title: Advertiser
description: Set the company or brand featured in each ad.
feature: Streaming Media
role: Developer
---

# Advertiser

>[!BEGINSHADEBOX]

*This page covers data collection for the **Advertiser** variable. See [Advertiser](/help/reporting/dimensions/advertiser.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The advertiser variable is the company or brand featured in the ad (for example, `"Ford"` or `"Coca-Cola"`). Use the variable to break out engagement and completion by advertiser.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.advertiser` |
| **XDM collection field** | [`xdm.mediaCollection.advertisingDetails.advertiser`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.ad.advertiser` |
| **Required** | No |
| **Sent with** | [Ad start](/help/implementation/events/ads/ad-start.md), ad close |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `advertiser` inside `xdm.mediaCollection.advertisingDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adStart",
    mediaCollection: {
      advertisingDetails: {
        name: "ad-2125",
        advertiser: "Ford"
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

>[!TAB iOS]

Pass the advertiser as a metadata key in the HashMap argument to `trackEvent(AdStart)`. Use `MediaConstants.AdMetadataKeys.ADVERTISER`.

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.AdMetadataKeys.ADVERTISER] = "Ford"

tracker.trackEvent(event: MediaEvent.AdStart, info: adObject, metadata: metadata)
```

>[!TAB Android]

Pass the advertiser as a metadata key in the HashMap argument to `trackEvent(AdStart)`. Use `MediaConstants.AdMetadataKeys.ADVERTISER`.

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.AdMetadataKeys.ADVERTISER] = "Ford"

tracker.trackEvent(Media.Event.AdStart, adObject, metadata)
```

>[!TAB Roku]

Set `advertiser` inside `xdm.mediaCollection.advertisingDetails` when calling `sendMediaEvent` for `media.adStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adStart",
        "mediaCollection": {
            "advertisingDetails": {
                "name": "ad-2125",
                "advertiser": "Ford"
            },
            "playhead": 0
        }
    }
})
```

>[!TAB Media Edge API]

Call the [adStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adstart) endpoint with `advertiser` inside `xdm.mediaCollection.advertisingDetails`:

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
          "advertiser": "Ford"
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

Pass the advertiser in the `contextData` object using `ADB.Media.AdMetadataKeys.Advertiser`:

```javascript
var contextData = {};
contextData[ADB.Media.AdMetadataKeys.Advertiser] = "Ford";

tracker.trackEvent(ADB.Media.Event.AdStart, adInfo, contextData);
```

>[!TAB Chromecast]

Set the advertiser using `ADBMobile.media.AdMetadataKeys.ADVERTISER` in the standard ad metadata object:

```javascript
var adInfo = ADBMobile.media.createAdObject("Ford F-150", "ad-2125", 1, 30);
var standardAdMetadata = {};
standardAdMetadata[ADBMobile.media.AdMetadataKeys.ADVERTISER] = "Sample advertiser";
adInfo[ADBMobile.media.MediaObjectKey.StandardAdMetadata] = standardAdMetadata;
ADBMobile.media.trackEvent(ADBMobile.media.Event.AdStart, adInfo, null);
```

>[!TAB Media Collection API]

Include `media.ad.advertiser` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adStart",
  "params": {
    "media.ad.advertiser": "Ford"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
