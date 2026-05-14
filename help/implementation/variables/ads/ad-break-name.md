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
| **XDM collection field** | [`mediaCollection.advertisingPodDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.ad.podFriendlyName` |
| **Required** | Yes (Mobile SDK); No (Edge, Media Collection API) |
| **Sent with** | Ad start, ad close |

## Web SDK

Set `friendlyName` inside `mediaCollection.advertisingPodDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) for `media.adBreakStart`:

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

## Mobile SDK

Pass the ad break name as the first (`name`) argument to `createAdBreakObject`, then track the ad-break-start event before the ad-start event.

**iOS (Swift)**

```swift
let adBreakObject = Media.createAdBreakObjectWith(name: "pre-roll",
                                              position: 1,
                                             startTime: 0)

tracker.trackEvent(event: MediaEvent.AdBreakStart, info: adBreakObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val adBreakObject = Media.createAdBreakObject("pre-roll",
                                              1L,
                                              0.0)

tracker.trackEvent(Media.Event.AdBreakStart, adBreakObject, null)
```

## Roku (BrightScript)

Set `friendlyName` inside `mediaCollection.advertisingPodDetails` when calling `sendMediaEvent` for `media.adBreakStart`:

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

## Media Edge API

Call the [adBreakStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adbreakstart) endpoint with `friendlyName` inside `mediaCollection.advertisingPodDetails`:

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

## Media SDK

Pass the ad break name as the first argument to `ADB.Media.createAdBreakObject`:

```javascript
var adBreakInfo = ADB.Media.createAdBreakObject(
  "pre-roll",
  1,
  0
);

tracker.trackEvent(ADB.Media.Event.AdBreakStart, adBreakInfo, null);
```

## Media Collection API

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
