---
title: Track Content Playback
description: Learn about tracking core playback, including tracking media load, media start, media pause, and media complete.
uuid: 7b8e2f76-bc4e-4721-8933-3e4453b01788
exl-id: 98ad2783-c9e3-48de-88df-8549f26114a0
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/cHrkCe0mQm8GlHwLVgf4cjF0VM8B1r3CRt39I2LB6kk
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
  - id: e992d880-33bc-4949-a648-aa7d410276cd
    internal-label: Validation
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---

# Track content playback

Core playback tracking covers media load, start, pause, resume, complete, and session end. Although not mandatory, buffering and seeking tracking are also core components of a complete playback implementation.

## Player events

| Player event | Action |
| --- | --- |
| Media load | Create media object; call SessionStart |
| Media start | Call Play |
| Pause | Call PauseStart |
| Resume from pause | Call Play |
| Media complete | Call SessionComplete |
| Media abort / unload | Call SessionEnd |
| Buffering starts | Call BufferStart |
| Buffering ends | Call Play (resume) |
| Seeking starts | Call SeekStart |
| Seeking ends | Call SeekComplete; then call Play |

## Implementation steps

1. **Identify when the user triggers playback** (user clicks play or autoplay fires). Create a media object with content name, ID, length, stream type, and media type. See [Content name](/help/implementation/variables/core/content-name.md), [Content ID](/help/implementation/variables/core/content-id.md), [Content length](/help/implementation/variables/core/content-length.md), [Stream type](/help/implementation/variables/core/stream-type.md), and [Content type](/help/implementation/variables/core/content-type.md) for field definitions.
1. **Optionally attach metadata** — standard metadata (show, season, episode, etc.) and custom context data variables. See [Show](/help/implementation/variables/standard-metadata/show.md), [Season](/help/implementation/variables/standard-metadata/season.md), [Episode](/help/implementation/variables/standard-metadata/episode.md), [Genre](/help/implementation/variables/standard-metadata/genre.md), and [Network](/help/implementation/variables/standard-metadata/network.md) for standard metadata key references.
1. **Call [Session start](/help/implementation/events/session/session-start.md)** to begin tracking the session. This loads the data and metadata and starts the time-to-start QoS measurement. SessionStart tracks the *intent* to play, not the first frame.
1. **Call [Play](/help/implementation/events/playback/play.md)** when the first frame of content renders on screen.
1. **Call [Pause start](/help/implementation/events/playback/pause-start.md)** when the player pauses. Call Play again when playback resumes. There is no separate resume event.
1. **Call [Session complete](/help/implementation/events/session/session-complete.md)** when the viewer reaches the end of content.
1. **Call [Session end](/help/implementation/events/session/session-end.md)** when the player is unloaded or the viewer abandons content without reaching the end. SessionEnd immediately closes the session; no further events can be tracked after it.

>[!IMPORTANT]
>
>`SessionEnd` marks the end of a tracking session. If the session was successfully watched to completion, call `SessionComplete` before `SessionEnd`. Any other tracking call is ignored after `SessionEnd`, except for `SessionStart` for a new session.

## Core playback

The following examples show a complete session flow — from session start through to content complete and session end.

For implementation details by platform, see [Session start](/help/implementation/events/session/session-start.md), [Play](/help/implementation/events/playback/play.md), [Pause start](/help/implementation/events/playback/pause-start.md), [Session complete](/help/implementation/events/session/session-complete.md), and [Session end](/help/implementation/events/session/session-end.md).

## Buffering

Buffer start signals that the player is waiting for data. Buffer end is inferred when you send a Play event after BufferStart (XDM-based APIs). On Mobile SDK, also call BufferComplete explicitly.

For implementation details, see [Buffer start](/help/implementation/events/playback/buffer-start.md).

## Seeking

Seek start signals that the viewer is scrubbing. Seek end is followed by Play to resume content playback.

For implementation details, see [Pause start](/help/implementation/events/playback/pause-start.md) (seek start) and [Play](/help/implementation/events/playback/play.md) (seek end).

## Handling app interrupts

Playback in a media application can be interrupted in a variety of ways — the user presses pause, the app goes to the background, a phone call arrives. Regardless of the cause, the tracking instructions are the same:

1. Call **PauseStart** when the application is interrupted (goes to background, media pauses, etc.).
1. Call **Play** when the application returns to the foreground and/or the media resumes playing.

>[!NOTE]
>
>Do not call SessionStart when the app returns from the background. Calling SessionStart causes the playback up to that point not to count towards total playback time, and earlier progress markers, segments, and chapter boundaries are lost.

**When should a paused session end?** If the application does not allow background playback, call PauseStart immediately and then call SessionEnd after approximately one minute in the background. The application cannot continue sending pause pings from the background, and holding the session open indefinitely provides a poor experience. If the application does support background playback (audio apps, video podcast apps), continue sending pings while in the background.

**Restarting after a long background period:** If the app was backgrounded long enough that the session expired (30-minute inactivity), call SessionEnd to cleanly close any lingering session, then call SessionStart to begin a new one when the viewer returns.

## Resuming inactive sessions

A session expires automatically if no events are received for 10 minutes or if there is no playhead movement for 30 minutes. If the user returns after a session has expired, call SessionStart again to open a new session.

**Resuming across devices (cross-device handoff):** When a viewer transfers playback between devices (for example, casting from a phone to a TV), use the resume flag to stitch the sessions together in Analytics reporting:

1. On the **source device**, call SessionEnd when the viewer initiates the cast. Do not call SessionComplete — the content is not finished.
1. On the **destination device**, call SessionStart with the resume flag set to `true` and pass the same content metadata and the playhead position from the source device.

Setting the resume flag causes Analytics to increment [Content resumes](/help/reporting/metrics/content-resumes.md) rather than [Media starts](/help/reporting/metrics/media-starts.md) for the second leg of the handoff.

**Manually resuming a previously closed session:** If the application stores user data and can resume a previously closed session, set the resume flag at session start. See [Session start](/help/implementation/events/session/session-start.md#resuming-a-session) for implementation details across all platforms.
