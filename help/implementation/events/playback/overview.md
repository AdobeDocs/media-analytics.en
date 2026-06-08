---
title: Track playback
description: Learn about playback events and how to implement play, pause, buffer, ping, and bitrate change tracking.
uuid: 4d73c47f-d0a4-4228-9040-d6432311c9eb
exl-id: af5f3372-a9a5-46ea-9c2f-81b0f5c96ccf
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/Cc5T13Z1S15MyG-CxpxMoHX-ckULmIe0dfUOe7650DE
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---

# Track playback

Playback events track state transitions in the media player throughout a session. They form the core of the event stream and apply to any content type.

## Player events

| Player event | Action |
| --- | --- |
| Media plays or resumes | Call Play |
| Media pauses | Call Pause start |
| Buffering begins | Call Buffer start |
| Buffering ends | Call Play |
| Bitrate changes | Call Bitrate change |
| Timer fires | Call Ping |

## Implementation steps

1. **Call [Play](play.md)** after [Session start](../session/session-start.md) when the first frame of content renders on screen. Also send Play when playback resumes after a pause or buffer stall. There is no separate resume event.
1. **Call [Pause start](pause-start.md)** when the user pauses playback. Send Play when playback resumes.
1. **Call [Buffer start](buffer-start.md)** when the player stalls waiting for data. On XDM-based APIs, buffer end is inferred when you send the next Play event. On Mobile SDK, also call `BufferComplete` explicitly when buffering resolves.
1. **Call [Ping](ping.md)** every 10 seconds during main content playback and every 1 second during ad playback. Ping keeps the session alive and records playhead movement. Mobile SDKs send pings automatically; all other platforms must send them manually.
1. **Call [Bitrate change](bitrate-change.md)** whenever the player negotiates a new bitrate. Include the current QoE data (bitrate, frames per second, dropped frames) so that the backend can compute [Average bitrate](/help/reporting/metrics/average-bitrate.md) and related quality metrics.
