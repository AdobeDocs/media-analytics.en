---
title: Streaming media events overview
description: Learn about media event types and the order in which they must be sent.
feature: Streaming Media
role: Developer
---

# Streaming media events

Streaming media tracking works by sending a sequence of event calls to an Adobe data collection endpoint, each representing a transition in the player's state. Every event belongs to an active session opened by a [Session start](session/session-start.md) call. Sessions close automatically through expiration or can be closed immediately with a [Session end](session/session-end.md) call.

Events are grouped into six categories (session, playback, ads, chapters, player state, and quality), each covering a distinct aspect of the media experience.

## Session events

Session events apply to any type of media tracking, including: video-on-demand, live streams, podcasts, and audiobooks. They define the boundaries of the tracking session itself. The most important session event is [Session start](session/session-start.md), as almost every other event type depends on the session ID that it generates. Send it as the very first event when a user initiates a session, such as when they press play or when the player begins autoplaying.

Once a session is open, use [Session complete](session/session-complete.md) or [Session end](session/session-end.md) to indicate how the viewing experience ended. Send Session complete when the viewer reaches the natural end of the content — the video finishes, the podcast episode ends, or the final chapter of an audiobook concludes. Session complete does not close the session; it remains open until it expires naturally, so any trailing events such as a final ping are still captured.

If the viewer leaves before reaching the end, send [Session end](session/session-end.md) to close the session immediately. Only send Session end when no additional events will follow — for example, when the player is destroyed or the page is unloaded. Session end is a hard close: once sent, the session is terminated and no further events can be tracked under it. In most cases, it is safer to allow the session to expire naturally. Examples include the viewer pausing indefinitely, the app going to the background, or content failing to load.

A session expires automatically if no events are received for 10 minutes, or if no playhead movement is detected for 30 minutes. If either condition is met and the viewer returns to the content, you must call Session start again to open a new session before sending any further events.

## Playback events

Playback events track state transitions in the media player throughout a session. They form the core of the event stream and apply to any content type.

The primary playback event is [Play](playback/play.md). After calling Session start, Play signals that content has begun playing — whether that is the initial start, an autoplay trigger, or any return to the playing state. [Pause start](playback/pause-start.md) signals that the user has paused playback. There is no dedicated resume event; when the viewer resumes, send Play again. Play works the same way after a buffering stall — send [Buffer start](playback/buffer-start.md) when the player stalls waiting for data, then follow with Play when buffering resolves.

Send [Ping](playback/ping.md) every 10 seconds during main content playback and every 1 second during ad playback. Ping keeps the session alive and records playhead movement. On Mobile SDKs, pings are sent automatically; on all other platforms they must be sent manually.

Send [Bitrate change](playback/bitrate-change.md) whenever the player's adaptive bitrate algorithm switches to a different quality level. Including the new bitrate value in the QoE data enables Average bitrate reporting.

## Ad events

Ad events track advertising within a media session. Common scenarios include pre-roll ads before a video begins, mid-roll ads inserted at intervals during a long-form video or live stream, and post-roll ads after content ends. A single ad break can contain one or multiple individual ads.

Every ad break follows the same structure. [Ad break start](ads/ad-break-start.md) opens the break and [Ad break complete](ads/ad-break-complete.md) closes it. These two events act as bookends that wrap all individual ad events. Within the break, send [Ad start](ads/ad-start.md) when each individual ad begins playing. Follow it with [Ad complete](ads/ad-complete.md) if the ad plays to its full length, or [Ad skip](ads/ad-skip.md) if the viewer selects the skip button. Omitting either bookend causes all ad events in the break to be ignored, and the ad duration is incorrectly attributed to main content.

The following example shows the correct event sequence for a single ad break containing three ads, where the viewer skipped the third:

1. Ad break start
2. Ad start
3. Ad complete
4. Ad start
5. Ad complete
6. Ad start
7. Ad skip
8. Ad break complete

## Chapter events

Chapter events are optional and track named content segments within a session. They are well suited to content naturally divided into discrete parts. Common examples include chapters in an audiobook, acts in a documentary, lessons in a video course, or segments in a podcast episode. Use chapter events when you want to understand viewer engagement at the segment level, such as identifying which chapters audiences tend to skip.

Send [Chapter start](chapters/chapter-start.md) when a chapter begins. If the viewer watches through to the end of the chapter, send [Chapter complete](chapters/chapter-complete.md). If the viewer seeks past the chapter boundary without watching it to completion, send [Chapter skip](chapters/chapter-skip.md) instead. A chapter must be closed with either Chapter complete or Chapter skip before a new one can open; chapters cannot overlap.

## Player state events

Player state events track how viewers interact with player controls throughout a session. They are useful for understanding accessibility feature usage, such as how often viewers enable closed captioning or mute. They also reveal viewing behavior patterns like fullscreen versus inline viewing and picture-in-picture multitasking.

The five trackable states are: `fullscreen`, `mute`, `closedCaptioning`, `pictureInPicture`, and `inFocus`. Send [State start](player-state/state-start.md) when the player enters any of these states and [State end](player-state/state-end.md) when it exits. Multiple states can be active at the same time; a viewer can be in fullscreen and muted simultaneously, and multiple states can be ended within the same event call.

## Error events

The [Error](error.md) event records a playback failure during a session — a failed stream request, a codec error, or an external delivery failure. Send it whenever a meaningful error occurs. An error event does not close the session; playback can continue and subsequent events are tracked under the same session. If the error is unrecoverable, follow it with Session end to explicitly close the session.
