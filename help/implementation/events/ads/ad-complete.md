---
title: Ad complete
description: Signal that an individual ad finished playing.
feature: Streaming Media
role: Developer
---

# Ad complete

The ad complete event signals that an individual ad finished playing. Send it after the ad plays to completion. If the viewer skips the ad, send [Ad skip](ad-skip.md) instead.

* **Prerequisites**: [Session start](../session/session-start.md), [Ad break start](ad-break-start.md), [Ad start](ad-start.md)
* **Associated metric**: [Ad completes](/help/reporting/metrics/ad-completes.md)

>[!IMPORTANT]
>
>This event must be surrounded by `adBreakStart` and `adBreakComplete` bookends, even when a single ad plays. Without these bookends, ad events are ignored and the ad duration is counted as main content duration.

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.adComplete"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adComplete",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 15
    }
  }
});
```

## Mobile SDK

Call `trackEvent` with the `AdComplete` event type.

**iOS (Swift)**

```swift
tracker.trackEvent(event: MediaEvent.AdComplete, info: nil, metadata: nil)
```

**Android (Kotlin)**

```kotlin
tracker.trackEvent(Media.Event.AdComplete, null, null)
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.adComplete"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adComplete",
        "mediaCollection": {
            "playhead": 15
        }
    }
})
```

## Media Edge API

Call the [adComplete](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adcomplete) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/adComplete?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.adComplete",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 15
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Call `trackEvent` with the `AdComplete` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.AdComplete, null, null);
```

## Media Collection API

Send an `adComplete` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 15, "ts": 1699523820000 },
  "eventType": "adComplete"
}
```
