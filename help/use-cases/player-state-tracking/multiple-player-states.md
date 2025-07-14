---
title: Updating multiple player states at once
description: This topic describes the Multiple Player State Tracking feature.
feature: Streaming Media
role: User, Admin, Data Engineer
exl-id: 7a512a81-a6d1-4d0c-a4fe-91e9b11419db
---
# Multiple Player States Tracking

Sometimes two player states start and end at the same time or the end of a state is also the beginning of another state as shown in the following image:

![Multiple player states](assets/multiple-player-states.png)

The current implementation allows both scenarios:
- `stateStart(pictureInPicture)` - t0
- `stateStart(mute)` - t0
- `stateEnd(mute)` - t1
- `stateEnd(pictureInPicture)` - t1
- `stateStart(fullScreen)` - t1
- `stateEnd(fullScreen)` - t2

However, this requires you to issue multiple `stateStart` and `stateEnd` events to signal multiple simultaneous state changes. In
order to optimize this common behavior, a new `statesUpdate` event type has been implemented, which ends a list of states
and starts a list of new states.

Using the new `statesUpdate` event, the above list of events becomes:
- `statesUpdate(statesEnd=[], statesStart=[pictureInPicture, mute])` - t0
- `statesUpdate(statesEnd=[mute, pictureInPicture], statesStart=[fullScreen])` - t1
- `statesUpdate(statesEnd=[fullScreen], statesStart=[])` - t2

The number of state updates calls has been reduced from six to three for the same behavior. The last event
could also have been a simple `stateEnd(fullScreen)`.

## Media Collection API implementation {#mpst-api}

You can use the Media Collection API to implement multiple player state tracking.

### Example

The following shows a Media Collection API implementation example for multiple player state tracking.

```
// statesUpdate (ex: mute and pictureInPicture are switched on)
http(s)://<Analytics_Visitor_Namespace>.hb-api.omtrdc.net/api/v1/sessions/<SID>/events
{
  "eventType": "statesUpdate",
  "params": {
    "statesStart": [
      {
        "media.state.name": "mute"
      },
      {
        "media.state.name": "pictureInPicture"
      }
    ]
  },
  "playerTime": {
    "playhead": 0,
    "ts": 1569999130627
  }
}
```

```
// statesUpdate (ex: mute and pictureInPicture are switched off, fullScreen is switched on)
http(s)://<Analytics_Visitor_Namespace>.hb-api.omtrdc.net/api/v1/sessions/<SID>/events
{
  "eventType": "statesUpdate",
  "params": {
    "statesEnd": [
      {
        "media.state.name": "mute"
      },
      {
        "media.state.name": "pictureInPicture"
      }
    ],
    "statesStart": [
      {
        "media.state.name": "fullScreen"
      }
    ]
  },
  "playerTime": {
    "playhead": 0,
    "ts": 1569999130627
  }
}
```

```
// statesUpdate (ex: fullScreen is switched off)
http(s)://<Analytics_Visitor_Namespace>.hb-api.omtrdc.net/api/v1/sessions/<SID>/events
{
  "eventType": "statesUpdate",
  "params": {
    "statesEnd": [
      {
        "media.state.name": "fullScreen"
      }
    ]
  },
  "playerTime": {
    "playhead": 0,
    "ts": 1569999130627
  }
}
```

## Media SDK implementation

There is no Media SDK implementation.
