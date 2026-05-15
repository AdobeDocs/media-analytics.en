---
title: Ad break complete
description: Signal that all ads in an ad break have finished.
feature: Streaming Media
role: Developer
---

# Ad break complete

The ad break complete event signals that all ads in an ad break have finished (either completed or skipped). It closes the ad break opened by [Ad break start](ad-break-start.md).

* **Prerequisites**: [Session start](../session/session-start.md), [Ad break start](ad-break-start.md)
* **Associated metric**: None

>[!IMPORTANT]
>
>Every `adBreakStart` must have a matching `adBreakComplete`. Without the closing bookend, ad events are ignored and ad duration is attributed to main content.

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.adBreakComplete"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adBreakComplete",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 0
    }
  }
});
```

## Mobile SDK

Call `trackEvent` with the `AdBreakComplete` event type.

**iOS (Swift)**

```swift
tracker.trackEvent(event: MediaEvent.AdBreakComplete, info: nil, metadata: nil)
```

**Android (Kotlin)**

```kotlin
tracker.trackEvent(Media.Event.AdBreakComplete, null, null)
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.adBreakComplete"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adBreakComplete",
        "mediaCollection": {
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [adBreakComplete](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adbreakcomplete) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/adBreakComplete?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.adBreakComplete",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 0
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Call `trackEvent` with the `AdBreakComplete` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.AdBreakComplete, null, null);
```

## Media Collection API

Send an `adBreakComplete` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "adBreakComplete"
}
```
