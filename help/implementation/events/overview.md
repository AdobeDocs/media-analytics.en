---
title: Streaming media events overview
description: Learn about media event types and the order in which they must be sent.
feature: Streaming Media
role: Developer
---

# Streaming media events

Streaming media tracking works by sending a sequence of event calls, each representing a player state transition, to an Adobe data collection endpoint. Every event belongs to an active session that begins with a [sessionStart](session/session-start.md) call and closes with [sessionComplete](session/session-complete.md) or [sessionEnd](session/session-end.md).

## Event workflow

The following ordered list shows the required event sequence for a typical VOD playback with a pre-roll ad and one chapter:

1. **[Session start](session/session-start.md)**: Always the first event; creates the session and returns a session ID
2. **[Ad break start](ads/ad-break-start.md)**: Required before any ad events
3. **[Ad start](ads/ad-start.md)** &rarr; **[Ad complete](ads/ad-complete.md)** (or **[Ad skip](ads/ad-skip.md)**)
4. **[Ad break complete](ads/ad-break-complete.md)**: Required after all ads in the break
5. **[Play](playback/play.md)**: Signals content playback begins or resumes
6. **[Chapter start](chapters/chapter-start.md)**: Optional; marks the beginning of a chapter
7. **[Ping](playback/ping.md)**: Sent every 10 seconds during main content, every 1 second during ads
8. **[Chapter complete](chapters/chapter-complete.md)**: Optional; marks the end of a chapter
9. **[Pause start](playback/pause-start.md)** &rarr; **[Play](playback/play.md)** (resume): For any pause
10. **[Buffer start](playback/buffer-start.md)** &rarr; **[Play](playback/play.md)** (resume): For any buffering
11. **[Session complete](session/session-complete.md)**: When the viewer reaches the end of the content

Use [Session end](session/session-end.md) instead of Session complete if the viewer abandons the session before reaching the end of the content.

## Session lifecycle

A session expires automatically if any of the following conditions are met:

* No events are received for **10 minutes**
* No playhead movement for **30 minutes**

## Event reference

| Event | Category | Associated metric |
| --- | --- | --- |
| [Session start](session/session-start.md) | Session | [Media starts](/help/reporting/metrics/media-starts.md) |
| [Session complete](session/session-complete.md) | Session | [Content completes](/help/reporting/metrics/content-completes.md) |
| [Session end](session/session-end.md) | Session | — |
| [Play](playback/play.md) | Playback | [Content starts](/help/reporting/metrics/content-starts.md) |
| [Pause start](playback/pause-start.md) | Playback | [Pause events](/help/reporting/metrics/pause-events.md) |
| [Buffer start](playback/buffer-start.md) | Playback | [Buffer events](/help/reporting/metrics/buffer-events.md) |
| [Bitrate change](playback/bitrate-change.md) | Playback | [Bitrate changes](/help/reporting/metrics/bitrate-changes.md) |
| [Ping](playback/ping.md) | Playback | — |
| [Ad break start](ads/ad-break-start.md) | Ads | — |
| [Ad start](ads/ad-start.md) | Ads | [Ad starts](/help/reporting/metrics/ad-starts.md) |
| [Ad complete](ads/ad-complete.md) | Ads | [Ad completes](/help/reporting/metrics/ad-completes.md) |
| [Ad skip](ads/ad-skip.md) | Ads | — |
| [Ad break complete](ads/ad-break-complete.md) | Ads | — |
| [Chapter start](chapters/chapter-start.md) | Chapters | [Chapter starts](/help/reporting/metrics/chapter-starts.md) |
| [Chapter complete](chapters/chapter-complete.md) | Chapters | [Chapter completes](/help/reporting/metrics/chapter-completes.md) |
| [Chapter skip](chapters/chapter-skip.md) | Chapters | — |
| [State start](player-state/state-start.md) | Player state | Varies by state |
| [State end](player-state/state-end.md) | Player state | Varies by state |
| [Error](error.md) | Quality | [Error impacted streams](/help/reporting/metrics/error-impacted-streams.md) |

>[!MORELIKETHIS]
>
>* [JSON validation schemas](/help/implementation/media-collection-api/mc-api-ref/mc-api-json-validation.md): Verify request payload structure for each event type
>* [Events request endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md): Media Collection API endpoint reference
>* [Sessions request endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md): Create a session before sending events
>* [Player state tracking](/help/use-cases/player-state-tracking/implementation-and-reporting.md): State start and state end implementation details
