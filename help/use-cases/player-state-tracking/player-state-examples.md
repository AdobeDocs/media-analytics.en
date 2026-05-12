---
title: Player State Tracking Examples
description: This topic includes examples of the Player State Tracking feature.
exl-id: a77bc882-ac03-40b4-ac64-87f26a09707b
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/eJ9Pb4tWQy0lRhkNXmexUyflt3qT0105FM--jAsGldQ
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# Player State Tracking Examples


## Long Pause example

When a video session has a pause duration that is longer than 30 minutes, the API requires a new session. When this occurs, the client should generate a new session ID. For both video sessions, the client should retain all the states that a player is in and send all the information as a `stateStart` event right after the `sessionStart` call.

`sessionStart → stateStart (fullscreen) → stateStart (mute) → pauseStart → (pings for 30 minutes) → sessionEnd`

After the `sessionEnd` is sent, a new video session must be started and the first API events would be:

`sessionStart → stateStart (fullscreen) → stateStart (mute) → ... other API events`

The long pause example shows that the player also stores its states, so they can be sent to the new video session.
