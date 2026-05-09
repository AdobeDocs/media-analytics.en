---
title: Closed captioning
description: Track when the viewer turns closed captioning on and off so the backend can report captioning engagement.
feature: Streaming Media
role: Developer
---

# Closed captioning

>[!BEGINSHADEBOX]

*This page covers data collection for the **Closed captioning** player state. See [Streams impacted by closed captioning](/help/reporting/variables/metrics/closed-captioning-streams-impacted.md), [Closed captioning counts](/help/reporting/variables/metrics/closed-captioning-count.md), and [Closed captioning total duration](/help/reporting/variables/metrics/closed-captioning-total-duration.md) for the corresponding reporting metrics.*

>[!ENDSHADEBOX]

The closed captioning player state tracks when the viewer turns captions on and off. Fire a state-start event when captions are enabled and a state-end event when captions are disabled. The backend computes three metrics from these events: streams impacted, count of state entries, and total time in state.

| Property | Value |
| --- | --- |
| **Context data variables** | `a.media.states.closedcaptioning.set`, `a.media.states.closedcaptioning.count`, `a.media.states.closedcaptioning.time` |
| **XDM collection field** | [`mediaCollection.statesStart[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) and [`mediaCollection.statesEnd[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) (entries with `name: "closedCaptioning"`) |
| **Required** | No |
| **Sent with** | State start, state end |

## Web SDK

Use [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) to send a `media.statesUpdate` event with the state added to `statesStart`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesStart: [{ name: "closedCaptioning" }],
      sessionID: "{sid}",
      playhead: 60
    }
  }
});
```

When the viewer disables captions, send another event with the state in `statesEnd`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesEnd: [{ name: "closedCaptioning" }],
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

## Mobile SDK

Use `tracker.trackPlayerStateStart()` and `tracker.trackPlayerStateEnd()` with the `MediaConstants.PlayerState.CLOSED_CAPTION` constant.

**iOS (Swift)**

```swift
let stateObject = Media.createStateObjectWith(stateName: MediaConstants.PlayerState.CLOSED_CAPTION)

tracker.trackPlayerStateStart(info: stateObject)
tracker.trackPlayerStateEnd(info: stateObject)
```

**Android (Kotlin)**

```kotlin
val stateObject = Media.createStateObject(MediaConstants.PlayerState.CLOSED_CAPTION)

tracker.trackPlayerStateStart(stateObject)
tracker.trackPlayerStateEnd(stateObject)
```

## Roku (BrightScript)

Use `sendMediaEvent` to send a `media.statesUpdate` event with the state added to `statesStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesStart": [{ "name": "closedCaptioning" }],
            "playhead": 60
        }
    }
})
```

When the viewer disables captions, send another event with the state in `statesEnd`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesEnd": [{ "name": "closedCaptioning" }],
            "playhead": 90
        }
    }
})
```

## Media Edge API

Call the [statesUpdate](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/statesupdate/) endpoint with `closedCaptioning` in `statesStart` (or `statesEnd` when the viewer disables captions):

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.statesUpdate",
      "mediaCollection": {
        "statesStart": [{ "name": "closedCaptioning" }],
        "sessionID": "{sid}",
        "playhead": 60
      }
    }
  }]
}
```

## Media SDK

Use `ADB.Media.createStateObject` and the `ADB.Media.PlayerState.ClosedCaptioning` constant:

```javascript
var stateObject = ADB.Media.createStateObject(ADB.Media.PlayerState.ClosedCaptioning);

tracker.trackPlayerStateStart(stateObject);
tracker.trackPlayerStateEnd(stateObject);
```

## Media Collection API

Send a `stateStart` POST request when captions are enabled, and a `stateEnd` POST when they are disabled:

```json
{
  "playerTime": { "playhead": 60, "ts": 1699523820000 },
  "eventType": "stateStart",
  "params": {
    "media.state.name": "closedCaptioning"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.
