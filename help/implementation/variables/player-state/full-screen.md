---
title: Full screen
description: Track when the viewer enters and exits full-screen playback so the backend can report full-screen engagement.
feature: Streaming Media
role: Developer
---

# Full screen

>[!BEGINSHADEBOX]

*This page covers data collection for the **Full screen** player state. See [Streams impacted by full screen](/help/reporting/variables/metrics/full-screen-streams-impacted.md), [Full screen counts](/help/reporting/variables/metrics/full-screen-count.md), and [Full screen total duration](/help/reporting/variables/metrics/full-screen-total-duration.md) for the corresponding reporting metrics.*

>[!ENDSHADEBOX]

The full-screen player state tracks when the viewer enters and exits full-screen playback. Fire a state-start event whenever the viewer enters full-screen and a state-end event when the viewer exits. The backend computes three metrics from these events: streams impacted, count of state entries, and total time in state.

| Property | Value |
| --- | --- |
| **Context data variables** | `a.media.states.fullscreen.set`, `a.media.states.fullscreen.count`, `a.media.states.fullscreen.time` |
| **XDM collection field** | [`mediaCollection.statesStart[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) and [`mediaCollection.statesEnd[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) (entries with `name: "fullscreen"`) |
| **Required** | No |
| **Sent with** | State start, state end |

## Web SDK

Use [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) to send a `media.statesUpdate` event with the state added to `statesStart`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesStart: [{ name: "fullscreen" }],
      sessionID: "{sid}",
      playhead: 60
    }
  }
});
```

When the viewer exits full-screen, send another event with the state in `statesEnd`:

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

## Mobile SDK

Use `tracker.trackPlayerStateStart()` and `tracker.trackPlayerStateEnd()` with the `MediaConstants.PlayerState.FULLSCREEN` constant.

**iOS (Swift)**

```swift
let stateObject = Media.createStateObjectWith(stateName: MediaConstants.PlayerState.FULLSCREEN)

tracker.trackPlayerStateStart(info: stateObject)
// ...later, when the user exits full-screen:
tracker.trackPlayerStateEnd(info: stateObject)
```

**Android (Kotlin)**

```kotlin
val stateObject = Media.createStateObject(MediaConstants.PlayerState.FULLSCREEN)

tracker.trackPlayerStateStart(stateObject)
// ...later, when the user exits full-screen:
tracker.trackPlayerStateEnd(stateObject)
```

## Roku (BrightScript)

Use `sendMediaEvent` to send a `media.statesUpdate` event with the state added to `statesStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesStart": [{ "name": "fullscreen" }],
            "playhead": 60
        }
    }
})
```

When the viewer exits full-screen, send another event with the state in `statesEnd`:

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

Call the [statesUpdate](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/statesupdate/) endpoint with `fullscreen` in `statesStart` (or `statesEnd` when the viewer exits):

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.statesUpdate",
      "mediaCollection": {
        "statesStart": [{ "name": "fullscreen" }],
        "sessionID": "{sid}",
        "playhead": 60
      }
    }
  }]
}
```

## Media SDK

Use `ADB.Media.createStateObject` and the `ADB.Media.PlayerState.FullScreen` constant:

```javascript
var stateObject = ADB.Media.createStateObject(ADB.Media.PlayerState.FullScreen);

tracker.trackPlayerStateStart(stateObject);
// ...later, when the user exits full-screen:
tracker.trackPlayerStateEnd(stateObject);
```

## Media Collection API

Send a `stateStart` POST request when the viewer enters full-screen, and a `stateEnd` POST when they exit:

```json
{
  "playerTime": { "playhead": 60, "ts": 1699523820000 },
  "eventType": "stateStart",
  "params": {
    "media.state.name": "fullscreen"
  }
}
```

```json
{
  "playerTime": { "playhead": 90, "ts": 1699523850000 },
  "eventType": "stateEnd",
  "params": {
    "media.state.name": "fullscreen"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
