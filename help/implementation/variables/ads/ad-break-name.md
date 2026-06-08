---
title: Ad break name
description: Set the friendly name of the parent ad break.
feature: Streaming Media
role: Developer
---

# Ad break name

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad break name** variable. See [Pod name](/help/reporting/dimensions/pod-name.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad break name variable is the friendly name of the ad break (for example, `"pre-roll"`, `"mid-roll-1"`, `"post-roll"`). The value is set on the ad-break object, not on individual ads.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.podFriendlyName` |
| **XDM collection field** | [`xdm.mediaCollection.advertisingPodDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.ad.podFriendlyName` |
| **Required** | Yes (Mobile SDK); No (Edge, Media Collection API) |
| **Sent with** | [Ad break start](/help/implementation/events/ads/ad-break-start.md), ad close |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `friendlyName` inside `xdm.mediaCollection.advertisingPodDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) for `media.adBreakStart`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adBreakStart",
    mediaCollection: {
      advertisingPodDetails: {
        friendlyName: "pre-roll",
        index: 1,
        offset: 0
      },
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

>[!TAB iOS]

Pass the ad break name as the first (`name`) argument to `createAdBreakObject`, then track the ad-break-start event before the ad-start event.

```swift
let adBreakObject = Media.createAdBreakObjectWith(name: "pre-roll",
                                              position: 1,
                                             startTime: 0)

tracker.trackEvent(event: MediaEvent.AdBreakStart, info: adBreakObject, metadata: nil)
```

>[!TAB Android]

Pass the ad break name as the first (`name`) argument to `createAdBreakObject`, then track the ad-break-start event before the ad-start event.

```kotlin
val adBreakObject = Media.createAdBreakObject("pre-roll",
                                              1L,
                                              0.0)

tracker.trackEvent(Media.Event.AdBreakStart, adBreakObject, null)
```

>[!TAB Roku Edge]

Set `friendlyName` inside `xdm.mediaCollection.advertisingPodDetails` when calling `sendMediaEvent` for `media.adBreakStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adBreakStart",
        "mediaCollection": {
            "advertisingPodDetails": {
                "friendlyName": "pre-roll",
                "index": 1,
                "offset": 0
            },
            "playhead": 0
        }
    }
})
```

>[!TAB Media Edge API]

Call the [adBreakStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adbreakstart) endpoint with `friendlyName` inside `xdm.mediaCollection.advertisingPodDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.adBreakStart",
      "mediaCollection": {
        "advertisingPodDetails": {
          "friendlyName": "pre-roll",
          "index": 1,
          "offset": 0
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

Pass the ad break name as the first argument to `ADB.Media.createAdBreakObject`:

```javascript
var adBreakInfo = ADB.Media.createAdBreakObject(
  "pre-roll",
  1,
  0
);

tracker.trackEvent(ADB.Media.Event.AdBreakStart, adBreakInfo, null);
```

>[!TAB Chromecast]

Pass the ad break name as the first argument to `ADBMobile.media.createAdBreakObject`:

```javascript
var adBreakInfo = ADBMobile.media.createAdBreakObject(
  "pre-roll",
  1,
  0
);
ADBMobile.media.trackEvent(ADBMobile.media.Event.AdBreakStart, adBreakInfo);
```

>[!TAB Roku 2.x]

Pass the ad break name as the first argument to `adb_media_init_adbreakinfo`. Note the Roku parameter order: `name, startTime, position`.

```brightscript
adb = ADBMobile()
adBreakInfo = adb_media_init_adbreakinfo("pre-roll", 0.0, 1)  ' name, startTime, position

adb.mediaTrackEvent(adb.MEDIA_AD_BREAK_START, adBreakInfo)
```

>[!TAB Media Collection API]

Include `media.ad.podFriendlyName` in the `params` object of your `adBreakStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adBreakStart",
  "params": {
    "media.ad.podFriendlyName": "pre-roll"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
