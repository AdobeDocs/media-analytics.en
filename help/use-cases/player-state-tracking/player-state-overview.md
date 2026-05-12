---
title: About Player State Tracking
description: Learn about the player state tracking feature including requirements and guidelines for implementing and reporting player states.
exl-id: c678e182-74e4-4f46-8596-7be57e645c66
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/R4ByVgEI65JyN-LFdMX1CCBs4zVyppVgebN9OJxJNMM
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
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# About Player State Tracking

To optimize your product experience and drive value for your business, it's important to understand customer behavior when viewing videos. This includes  the time spent within different player states.  It's also important to have the flexibility to create and measure new player states and events as needed.

Player State Tracking provides the capability to capture viewer interaction during playback using a standard set of solution variables for full screen, closed captioning, mute, picture in picture, and in focus.  Player State Tracking also provides the flexibility to create custom player states. You can use Player State Tracking variables for reporting in Analysis Workspace.  

To capture changes to the player state, Player State Tracking updates the video measurement metadata. For example, to determine the "true" video engagement, Player State Tracking measures time spent with the sound on versus the passive or non-engaged video views when the sound is off or the time spent in Normal versus Full Screen mode.

Player State Tracking delivers the following benefits:

* Provides standard variables that measure common states such as full screen or closed captioning
* Provides customizable variables to measure custom states during a playback session
* Measures time spent within a custom player state
* Measures multiple states that may be concurrent

![Player state tracking](assets/player_state_tracking.png)

## Requirements

Player State Tracking requires one of the following for data collection:
* Media JS SDK 3.0+
* Chromecast 3.0 SDK for Adobe Marketing Cloud Solutions
* Media Analytics Extension (for use with the Adobe Experience Platform (AEP) SDK)
   * Web: Adobe Media Analytics (3.x SDK) for Audio and Video v1.0+
   * Mobile: Adobe Media Analytics for Audio and Video v2.0+
* Media Collection API

## Guidelines

Before implementing Player state tracking consider the following guidelines.

* The player state is computed across all playback states (no splitting).
* You can measure multiple player states at the same time.
* The maximum number of player states that can be tracked during a playback is 10.
* Player state metrics are sent to Analytics for reporting on the Media Close call only.
* Knowledge of the application status isn’t maintained after a state stops. After a state ends, the state must be started again to continue tracking. For every new playback state, the state of the player must be started again. 
* Player states are captured for each individual playback session—the player state is not computed across playbacks.
