---
title: Streaming Media Event Types and Descriptions
description: "What are the Media Collection event types and descriptions? "
uuid: bc4f75a7-ea22-47eb-a50d-5f41274c6d41
exl-id: f2919e69-8b03-45b4-b9cd-365222a061e0
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/gqlCzqKd3F7N2-7WE727Ygl-4wheVjObgnx-ydLbgZk
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
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Event types and descriptions{#event-types-and-descriptions}

## sessionStart

Sent with the `sessions` call. When the response returns, you extract the Session ID from the Location header and use it for subsequent event calls to the Collection server.

## play

Sent when the player changes state to "playing" from another state (i.e., the `on('Playing')` callback is triggered by the player). Other states from which the player moves to "playing" include "buffering", the user resumed from "paused", the player recovered from an error, autoplay, and so on. 

## ping

* **Main Content -** Must be sent every 10 seconds during main content playback, regardless of other API events that have been sent. The first ping event should fire 10 seconds after main content playback has begun. 
* **Ad Content -** Must be sent every 1 second during ad tracking.

Ping events should *not* include the `params` map in the request body.

## bitrateChange

Sent when the bitrage changes.

## bufferStart

Sent when buffering starts. There is no `bufferResume` event type. A `bufferResume` is inferred when you send a `play` event after `bufferStart`.

## pauseStart

Sent when the user presses Pause. There is no `resume` event type. A `resume` is inferred when you send a `play` event after a `pauseStart`.

## adBreakStart

Signals the start of an ad break 

## adStart

Signals the start of an ad 

## adComplete

Signals the completion of an ad break

## adSkip

Signals an ad skip

## adBreakComplete

Signals the completion of an ad break

## chapterStart

Signals the start of a chapter segment

## chapterSkip

Signals a chapter skip

## chapterComplete

Signals the completion of a chapter

## error

Signals an error occurred.

## sessionEnd

This is used to notify the Media Analytics backend to immediately close the session when the user has abandoned their viewing of the content and they are unlikely to return.

If a `sessionEnd` is not sent, an abandoned session will [time-out normally](../mc-api-impl/mc-api-timeout.md) (either after no events are received for 10 minutes, or when no playhead movement occurs for 30 minutes). Additionally, all subsequent Media Calls made with that Session ID will be dropped.

## sessionComplete

Sent when the end of the main content is reached

>[!IMPORTANT]
>
>You should refer to the [JSON validation schemas](mc-api-json-validation.md) for each event type, to verify correct event parameter types and requirements.

## stateStart

Signals the start of player state tracking. 

For more information, see [Implementation and reporting](/help/use-cases/player-state-tracking/implementation-and-reporting.md).

## stateEnd

Signals the end of player state tracking.

For more information, see [Implementation and reporting](/help/use-cases/player-state-tracking/implementation-and-reporting.md).
