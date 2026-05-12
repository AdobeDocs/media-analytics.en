---
title: Implementation and Reporting
description: Learn about how to implement the player state tracking feature including .
exl-id: 19a97c9b-14d1-4f11-bb0a-3a1ad6f949da
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/NzekVHZYctiEjAWDpRhIdiw74amAX3wTX-z2nZDgvIw
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: c153fd90-23e1-4614-81d3-3cc7571227f7
    internal-label: Analysis Workspace
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
  - id: f836f655-eebe-4b76-82bc-697955ec1ce3
    internal-label: Calculated Metrics
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Implementation and reporting

During a playback session, each state occurrence (start-to-end) must be tracked individually. The Media SDK and the Media Collection API provide tracking methods for this capability.

The Media SDK includes two methods for custom state tracking:

`trackStateStart("state_name")`

`trackStateClose("state_name")`


The Media Collection API includes two events that have `media.stateName` as the required parameter:

`stateStart` and `stateEnd`

## Media SDK implementation

Player State Starts

```
// StateStart (ex: Mute is switched on)
var stateObject = ADB.Media.createStateObject(ADB.Media.PlayerState.Mute);
tracker.trackEvent(ADB.Media.Event.StateStart, stateObject);
```

Player State Ends

```
// StateEnd (ex: Mute is switched off)
tracker.trackEvent(ADB.Media.Event.StateEnd, stateObject);
```


## Media Collection API implementation

Player State Starts

```
// StateStart (ex: Mute is switched on)
http(s)://<Analytics_Visitor_Namespace>.hb-api.omtrdc.net/api/v1/sessions/<SID>/events
{
  "eventType": "stateStart",
  "params": {
    "media.state.name": "mute"
  },
  "playerTime": {
    "playhead": 0,
    "ts": 1569999130627
  }
}
```

Player State Ends

```
// StateEnd (ex: Mute is switched off)
http(s)://<Analytics_Visitor_Namespace>.hb-api.omtrdc.net/api/v1/sessions/<SID>/events

{
  "eventType": "stateEnd",
  "params": {
    "media.state.name": "mute"
  },
  "playerTime": {
    "playhead": 600,
    "ts": 1569999730638
  }
}
```

## State Metrics

The metrics provided for each individual state are computed and pushed to Adobe Analytics as Context Data parameters and stored for reporting purposes. Three metrics are available for each state:

* `a.media.states.[state.name].set = true` — Set to true if the state was set at least once per each specific playback of a stream.
* `a.media.states.[state.name].count = 4` — Identifies the number of occurrences of a state during per each individual playback of a stream
* `a.media.states.[state.name].time = 240` — Identifies the total state duration in seconds per each individual playback of a stream

## Reporting

All player state metrics can be used for any reporting visualization available in Analysis Workspace or a component (segment, calculated metrics) once a report suite is enabled for player state tracking. These metrics could be enabled from the Admin Console for each individual report using Media Reporting Setup (Edit Settings > Media Management > Media Reporting).

![](assets/report-setup.png)

In Analysis Workspace, all new properties are located in the metrics panel. For example, you can search by `full screen` to view the full screen data in the metrics panel.

![](assets/full-screen-report.png)

## Importing player stated metrics to Adobe Experience Platform

Data stored in Analytics could be used for any purpose and the player state metrics can be imported into Adobe Experience Platform using XDM and used with Customer Journey Analytics. The standard state properties have specific properties while the custom states are properties are available using the custom events.
