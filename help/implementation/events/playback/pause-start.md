---
title: Pause start
description: Signal that the user paused media playback.
feature: Streaming Media
role: Developer
---

# Pause start

The pause start event signals that the user paused playback. There is no separate resume event; send a [Play](play.md) event when playback resumes.

* **Prerequisites**: [Session start](../session/session-start.md)
* **Associated metric**: [Pause events](/help/reporting/metrics/pause-events.md)

>[!NOTE]
>
>There is no resume event type. Resume is inferred when you send a [`play`](play.md) event after `pauseStart`.

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.pauseStart"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.pauseStart",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 30
    }
  }
});
```

## Mobile SDK

Call `trackPause` when the user pauses playback.

**iOS (Swift)**

```swift
tracker.trackPause()
```

**Android (Kotlin)**

```kotlin
tracker.trackPause()
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.pauseStart"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.pauseStart",
        "mediaCollection": {
            "playhead": 30
        }
    }
})
```

## Media Edge API

Call the [pauseStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/pausestart/) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/pauseStart?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.pauseStart",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 30
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Call `trackPause` when the user pauses playback:

```javascript
tracker.trackPause();
```

## Media Collection API

Send a `pauseStart` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 30, "ts": 1699523820000 },
  "eventType": "pauseStart"
}
```
