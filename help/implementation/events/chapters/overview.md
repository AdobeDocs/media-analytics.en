---
title: Track Chapters and Segments
description: How to implement chapter and segment tracking with the Media SDK.
uuid: 3fe32425-5e2a-4886-8fec-d91d15671bb0
exl-id: d213b633-be3b-4eb8-be71-0ef55e78a570
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/PAadkD9nJ7IRf7LdsNzIWtFp0yv54x0xV-Js-ona0Lg
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

# Track chapters and segments

Chapter and segment tracking is available for custom-defined media chapters or segments. Some common uses for chapter tracking are to define custom segments based on media content (such as baseball innings), or to define content segments between ad breaks. Chapter tracking is **not** required for core media tracking implementations.

Chapter tracking includes chapter starts, chapter completes, and chapter skips. Use the media player API with customized segmentation logic to identify chapter events and to populate the chapter variables.

## Player events

| Player event | Action |
| --- | --- |
| Chapter start | Create chapter object; call ChapterStart |
| Chapter complete | Call ChapterComplete |
| Chapter skip | Call ChapterSkip |

## Implementation steps

1. Identify when the chapter start event occurs and create the chapter object. See [Chapter name](/help/implementation/variables/chapters/chapter-name.md), [Chapter position](/help/implementation/variables/chapters/chapter-position.md), [Chapter length](/help/implementation/variables/chapters/chapter-length.md), and [Chapter offset](/help/implementation/variables/chapters/chapter-offset.md) for field definitions.
1. Optionally create context data variables for custom chapter metadata.
1. Call [Chapter start](/help/implementation/events/chapters/chapter-start.md) to begin tracking the chapter.
1. When playback reaches the chapter end boundary, call [Chapter complete](/help/implementation/events/chapters/chapter-complete.md).
1. If the user skips the chapter before completion, call [Chapter skip](/help/implementation/events/chapters/chapter-skip.md).
1. For additional chapters, repeat steps 1 through 5.
