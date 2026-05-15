---
title: Ad break start time
description: Set the start time (offset) of the ad break inside the content, in seconds.
feature: Streaming Media
role: Developer
---

# Ad break start time

>[!BEGINSHADEBOX]

*This page covers data collection for the **Ad break start time** variable. See [Pod position](/help/reporting/dimensions/pod-position.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The ad break start time variable is the offset of the ad break inside the content, measured in seconds. For a pre-roll the value is `0`; for a mid-roll the value is the playhead position at which the break begins.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.ad.podSecond` |
| **XDM collection field** | [`mediaCollection.advertisingPodDetails.offset`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.ad.podSecond` |
| **Required** | Yes |
| **Sent with** | [Ad break start](/help/implementation/events/ads/ad-break-start.md), ad close |

## Web SDK

Set `offset` inside `mediaCollection.advertisingPodDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adBreakStart",
    mediaCollection: {
      advertisingPodDetails: {
        friendlyName: "mid-roll-1",
        index: 2,
        offset: 90
      },
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

## Mobile SDK

Pass the start time in seconds as the third argument to `createAdBreakObject`.

**iOS (Swift)**

```swift
let adBreakObject = Media.createAdBreakObjectWith(name: "mid-roll-1",
                                              position: 2,
                                             startTime: 90)

tracker.trackEvent(event: MediaEvent.AdBreakStart, info: adBreakObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val adBreakObject = Media.createAdBreakObject("mid-roll-1",
                                              2L,
                                              90.0)

tracker.trackEvent(Media.Event.AdBreakStart, adBreakObject, null)
```

## Roku (BrightScript)

Set `offset` inside `mediaCollection.advertisingPodDetails` when calling `sendMediaEvent` for `media.adBreakStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adBreakStart",
        "mediaCollection": {
            "advertisingPodDetails": {
                "friendlyName": "mid-roll-1",
                "index": 2,
                "offset": 90
            },
            "playhead": 90
        }
    }
})
```

## Media Edge API

Call the [adBreakStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adbreakstart) endpoint with `offset` inside `mediaCollection.advertisingPodDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.adBreakStart",
      "mediaCollection": {
        "advertisingPodDetails": {
          "index": 2,
          "offset": 90
        },
        "sessionID": "{sid}",
        "playhead": 90
      }
    }
  }]
}
```

## Media SDK

Pass the start time as the third argument to `ADB.Media.createAdBreakObject`:

```javascript
var adBreakInfo = ADB.Media.createAdBreakObject(
  "mid-roll-1",
  2,
  90
);

tracker.trackEvent(ADB.Media.Event.AdBreakStart, adBreakInfo, null);
```

## Media Collection API

Include `media.ad.podSecond` in the `params` object of your `adBreakStart` POST request:

```json
{
  "playerTime": { "playhead": 90, "ts": 1699523820000 },
  "eventType": "adBreakStart",
  "params": {
    "media.ad.podSecond": 90
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
