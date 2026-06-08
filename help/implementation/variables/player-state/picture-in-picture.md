---
title: Picture in picture
description: Track when the viewer enters and exits picture-in-picture playback so the backend can report PiP engagement.
feature: Streaming Media
role: Developer
---

# Picture in picture

>[!BEGINSHADEBOX]

*This page covers data collection for the **Picture in picture** player state. See [Streams impacted by picture in picture](/help/reporting/metrics/picture-in-picture-streams-impacted.md), [Picture in picture counts](/help/reporting/metrics/picture-in-picture-count.md), and [Picture in picture total duration](/help/reporting/metrics/picture-in-picture-total-duration.md) for the corresponding reporting metrics.*

>[!ENDSHADEBOX]

The picture in picture player state tracks when the viewer enters and exits picture-in-picture playback. Fire a state-start event when picture-in-picture begins and a state-end event when it ends. The backend computes three metrics from these events: streams impacted, count of state entries, and total time in state.

| Property | Value |
| --- | --- |
| **Context data variables** | `a.media.states.pictureinpicture.set`, `a.media.states.pictureinpicture.count`, `a.media.states.pictureinpicture.time` |
| **XDM collection field** | [`xdm.mediaCollection.statesStart[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) and [`xdm.mediaCollection.statesEnd[]`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-collection-details) (entries with `name: "pictureInPicture"`) |
| **Audience Manager traits** | `c_contextdata.a.media.states.pictureinpicture.set`, `c_contextdata.a.media.states.pictureinpicture.count`, `c_contextdata.a.media.states.pictureinpicture.time` |
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
      statesStart: [{ name: "pictureInPicture" }],
      sessionID: "{sid}",
      playhead: 60
    }
  }
});
```

When the viewer exits picture-in-picture, send another event with the state in `statesEnd`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.statesUpdate",
    mediaCollection: {
      statesEnd: [{ name: "pictureInPicture" }],
      sessionID: "{sid}",
      playhead: 90
    }
  }
});
```

>[!TAB iOS]

Use `tracker.trackPlayerStateStart()` and `tracker.trackPlayerStateEnd()` with the `MediaConstants.PlayerState.PICTURE_IN_PICTURE` constant.

```swift
let stateObject = Media.createStateObjectWith(stateName: MediaConstants.PlayerState.PICTURE_IN_PICTURE)

tracker.trackPlayerStateStart(info: stateObject)
tracker.trackPlayerStateEnd(info: stateObject)
```

>[!TAB Android]

Use `tracker.trackPlayerStateStart()` and `tracker.trackPlayerStateEnd()` with the `MediaConstants.PlayerState.PICTURE_IN_PICTURE` constant.

```kotlin
val stateObject = Media.createStateObject(MediaConstants.PlayerState.PICTURE_IN_PICTURE)

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
            "statesStart": [{ "name": "pictureInPicture" }],
            "playhead": 60
        }
    }
})
```

When the viewer exits picture-in-picture, send another event with the state in `statesEnd`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.statesUpdate",
        "mediaCollection": {
            "statesEnd": [{ "name": "pictureInPicture" }],
            "playhead": 90
        }
    }
})
```

>[!TAB Media Edge API]

Call the [statesUpdate](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/statesupdate/) endpoint with `pictureInPicture` in `statesStart` (or `statesEnd` when the viewer exits PiP):

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.statesUpdate",
      "mediaCollection": {
        "statesStart": [{ "name": "pictureInPicture" }],
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

Use `ADB.Media.createStateObject` and the `ADB.Media.PlayerState.PictureInPicture` constant:

```javascript
var stateObject = ADB.Media.createStateObject(ADB.Media.PlayerState.PictureInPicture);

tracker.trackPlayerStateStart(stateObject);
tracker.trackPlayerStateEnd(stateObject);
```

>[!TAB Chromecast]

Use `ADBMobile.media.createStateObject` with the `"pictureInPicture"` string directly, as Chromecast does not have named `PlayerState` constants:

```javascript
var stateObject = ADBMobile.media.createStateObject("pictureInPicture");
ADBMobile.media.trackEvent(ADBMobile.media.Event.StateStart, stateObject);
// When the viewer exits picture-in-picture:
ADBMobile.media.trackEvent(ADBMobile.media.Event.StateEnd, stateObject);
```

>[!TAB Roku 2.x]

Player state tracking is not available in the Roku 2.x SDK. To track player states, use the [Roku Edge SDK](/help/implementation/edge/roku.md).

>[!TAB Media Collection API]

Send a `stateStart` POST request when picture-in-picture begins, and a `stateEnd` POST when it ends:

```json
{
  "playerTime": { "playhead": 60, "ts": 1699523820000 },
  "eventType": "stateStart",
  "params": {
    "media.state.name": "pictureInPicture"
  }
}
```

See the [Media Collection API events reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) for the full request structure.

>[!ENDTABS]
