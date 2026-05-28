---
title: Ad skip
description: Signal that the viewer skipped an ad.
feature: Streaming Media
role: Developer
---

# Ad skip

The ad skip event signals that the viewer skipped an ad before it finished. Send it when the viewer selects the skip button. Send [Ad complete](ad-complete.md) instead if the ad plays to completion.

* **Prerequisites**: [Session start](../session/session-start.md), [Ad break start](ad-break-start.md), [Ad start](ad-start.md)
* **Associated metric**: None

>[!IMPORTANT]
>
>This event must be surrounded by `adBreakStart` and `adBreakComplete` bookends, even when a single ad plays. Without these bookends, ad events are ignored and the ad duration is counted as main content duration.

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.adSkip"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.adSkip",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 5
    }
  }
});
```

>[!TAB iOS]

Call `trackEvent` with the `AdSkip` event type.

```swift
tracker.trackEvent(event: MediaEvent.AdSkip, info: nil, metadata: nil)
```

>[!TAB Android]

Call `trackEvent` with the `AdSkip` event type.

```kotlin
tracker.trackEvent(Media.Event.AdSkip, null, null)
```

>[!TAB Roku]

Call `sendMediaEvent` with `eventType: "media.adSkip"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.adSkip",
        "mediaCollection": {
            "playhead": 5
        }
    }
})
```

>[!TAB Media Edge API]

Call the [adSkip](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ads/#adskip) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/adSkip?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.adSkip",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 5
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Call `trackEvent` with the `AdSkip` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.AdSkip, null, null);
```

>[!TAB Chromecast]

Call `trackEvent` with the `AdSkip` event type:

```javascript
ADBMobile.media.trackEvent(ADBMobile.media.Event.AdSkip);
```

>[!TAB Media Collection API]

Send an `adSkip` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 5, "ts": 1699523820000 },
  "eventType": "adSkip"
}
```

>[!ENDTABS]
