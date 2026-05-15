---
title: State end
description: Signal that the media player exited a tracked player state.
feature: Streaming Media
role: Developer
---

# State end

The state end event signals that the media player exited a tracked state such as full screen, mute, or closed captioning. Send it to close a state opened by [State start](state-start.md). States can be started and ended in the same event call. A player can exit multiple states simultaneously.

Valid state names: `fullscreen`, `mute`, `closedCaptioning`, `pictureInPicture`, `inFocus`

| Property | Value |
| --- | --- |
| **Prerequisites** | [Session start](../session/session-start.md), [State start](state-start.md) |
| **Associated metric** | Varies by state; see [Player state tracking](/help/use-cases/player-state-tracking/implementation-and-reporting.md) |

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.statesUpdate"` and the state name in `statesEnd`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesEnd: [{ name: "fullscreen" }],
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

States can be started and ended in the same call:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesStart: [{ name: "mute" }],
      statesEnd: [{ name: "fullscreen" }],
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

## Mobile SDK

Use `trackPlayerStateEnd` with a state object created from the appropriate `MediaConstants.PlayerState` constant.

**iOS (Swift)**

```swift
let stateObject = Media.createStateObjectWith(stateName: MediaConstants.PlayerState.FULLSCREEN)

tracker.trackEvent(event: MediaEvent.StateEnd, info: stateObject, metadata: nil)
```

**Android (Kotlin)**

```kotlin
val stateObject = Media.createStateObject(MediaConstants.PlayerState.FULLSCREEN)

tracker.trackEvent(Media.Event.StateEnd, stateObject, null)
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.statesUpdate"` and the state name in `statesEnd`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesEnd": [{ "name": "fullscreen" }],
            "playhead": 90
        }
    }
})
```

## Media Edge API

Call the [statesUpdate](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/statesupdate/) endpoint with the state name in `statesEnd`:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/statesUpdate?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.statesUpdate",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 90,
        "statesEnd": [{ "name": "fullscreen" }]
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Use `ADB.Media.createStateObject` with the appropriate `ADB.Media.PlayerState` constant:

```javascript
var stateObject = ADB.Media.createStateObject(ADB.Media.PlayerState.Fullscreen);

tracker.trackPlayerStateEnd(stateObject);
```

## Media Collection API

Send a `stateEnd` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 90, "ts": 1699523820000 },
  "eventType": "stateEnd",
  "params": {
    "media.state.name": "fullscreen"
  }
}
```
