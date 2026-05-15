---
title: Buffer start
description: Signal that the media player entered a buffering state.
feature: Streaming Media
role: Developer
---

# Buffer start

The buffer start event signals that the media player entered a buffering state.

* **Prerequisites**: [Session start](../session/session-start.md)
* **Associated metric**: [Buffer events](/help/reporting/metrics/buffer-events.md)

>[!NOTE]
>
>**XDM-based APIs (Web SDK, Roku, Media Edge API, Media Collection API):** There is no buffer resume event type; buffer end is inferred when you send a [`play`](play.md) event after `bufferStart`.
>
>**Mobile SDK:** Call `trackEvent(BufferComplete)` when the player exits buffering, then call `trackPlay()` to resume playback.

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.bufferStart"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.bufferStart",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 45
    }
  }
});
```

## Mobile SDK

Call `trackEvent` with `BufferStart` when the player enters a buffering state, and `BufferComplete` when it exits.

**iOS (Swift)**

```swift
// Buffer starts
tracker.trackEvent(event: MediaEvent.BufferStart, info: nil, metadata: nil)

// Buffer ends
tracker.trackEvent(event: MediaEvent.BufferComplete, info: nil, metadata: nil)
```

**Android (Kotlin)**

```kotlin
// Buffer starts
tracker.trackEvent(Media.Event.BufferStart, null, null)

// Buffer ends
tracker.trackEvent(Media.Event.BufferComplete, null, null)
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.bufferStart"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.bufferStart",
        "mediaCollection": {
            "playhead": 45
        }
    }
})
```

## Media Edge API

Call the [bufferStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bufferstart/) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/bufferStart?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.bufferStart",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 45
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Call `trackEvent` with the `BufferStart` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.BufferStart, null, null);
```

## Media Collection API

Send a `bufferStart` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 45, "ts": 1699523820000 },
  "eventType": "bufferStart"
}
```
