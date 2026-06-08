---
title: In focus
description: Track when the player is in focus on the viewer's screen so the backend can report focus engagement.
feature: Streaming Media
role: Developer
---

# In focus

>[!BEGINSHADEBOX]

*This page covers data collection for the **In focus** player state. See [Streams impacted by in focus](/help/reporting/metrics/in-focus-streams-impacted.md), [In focus counts](/help/reporting/metrics/in-focus-count.md), and [In focus total duration](/help/reporting/metrics/in-focus-total-duration.md) for the corresponding reporting metrics.*

>[!ENDSHADEBOX]

The in focus player state tracks when the player has the viewer's attention. Fire a state-start event when the player gains focus (typically when the player tab or window becomes active) and a state-end event when the player loses focus. The backend computes three metrics from these events: streams impacted, count of state entries, and total time in state.

| Property | Value |
| --- | --- |
| **Context data variables** | `a.media.states.infocus.set`, `a.media.states.infocus.count`, `a.media.states.infocus.time` |
| **XDM collection field** | [`xdm.mediaCollection.statesStart[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) and [`xdm.mediaCollection.statesEnd[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) (entries with `name: "inFocus"`) |
| **Audience Manager traits** | `c_contextdata.a.media.states.infocus.set`, `c_contextdata.a.media.states.infocus.count`, `c_contextdata.a.media.states.infocus.time` |
| **Required** | No |
| **Sent with** | [State start](/help/implementation/events/player-state/state-start.md), [state end](/help/implementation/events/player-state/state-end.md) |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Use [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) to send a `media.statesUpdate` event with the state added to `statesStart`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesStart: [{ name: "inFocus" }],
      sessionID: "{sid}",
      playhead: 60
    }
  }
});
```

When the player loses focus, send another event with the state in `statesEnd`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesEnd: [{ name: "inFocus" }],
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

>[!TAB iOS]

Use `tracker.trackPlayerStateStart()` and `tracker.trackPlayerStateEnd()` with the `MediaConstants.PlayerState.IN_FOCUS` constant.

```swift
let stateObject = Media.createStateObjectWith(stateName: MediaConstants.PlayerState.IN_FOCUS)

tracker.trackPlayerStateStart(info: stateObject)
tracker.trackPlayerStateEnd(info: stateObject)
```

>[!TAB Android]

Use `tracker.trackPlayerStateStart()` and `tracker.trackPlayerStateEnd()` with the `MediaConstants.PlayerState.IN_FOCUS` constant.

```kotlin
val stateObject = Media.createStateObject(MediaConstants.PlayerState.IN_FOCUS)

tracker.trackPlayerStateStart(stateObject)
tracker.trackPlayerStateEnd(stateObject)
```

>[!TAB Roku Edge]

Use `sendMediaEvent` to send a `media.statesUpdate` event with the state added to `statesStart`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesStart": [{ "name": "inFocus" }],
            "playhead": 60
        }
    }
})
```

When the player loses focus, send another event with the state in `statesEnd`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesEnd": [{ "name": "inFocus" }],
            "playhead": 90
        }
    }
})
```

>[!TAB Media Edge API]

Call the [statesUpdate](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/statesupdate/) endpoint with `inFocus` in `statesStart` (or `statesEnd` when the player loses focus):

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.statesUpdate",
      "mediaCollection": {
        "statesStart": [{ "name": "inFocus" }],
        "sessionID": "{sid}",
        "playhead": 60
      }
    }
  }]
}
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Use `ADB.Media.createStateObject` and the `ADB.Media.PlayerState.InFocus` constant:

```javascript
var stateObject = ADB.Media.createStateObject(ADB.Media.PlayerState.InFocus);

tracker.trackPlayerStateStart(stateObject);
tracker.trackPlayerStateEnd(stateObject);
```

>[!TAB Chromecast]

Use `ADBMobile.media.createStateObject` with the `"inFocus"` string directly, as Chromecast does not have named `PlayerState` constants:

```javascript
var stateObject = ADBMobile.media.createStateObject("inFocus");
ADBMobile.media.trackEvent(ADBMobile.media.Event.StateStart, stateObject);
// When the player loses focus:
ADBMobile.media.trackEvent(ADBMobile.media.Event.StateEnd, stateObject);
```

>[!TAB Roku 2.x]

Player state tracking is not available in the Roku 2.x SDK. To track player states, use the [Roku Edge SDK](/help/implementation/edge/roku.md).

>[!TAB Media Collection API]

Send a `stateStart` POST request when the player gains focus, and a `stateEnd` POST when it loses focus:

```json
{
  "playerTime": { "playhead": 60, "ts": 1699523820000 },
  "eventType": "stateStart",
  "params": {
    "media.state.name": "inFocus"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
