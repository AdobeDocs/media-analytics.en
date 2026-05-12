---
title: About Standard and Custom States
description: Learn about the player state tracking feature including requirements and guidelines for implementing and reporting standard and custom player states.
exl-id: 3c492055-d471-4147-aa78-b058d6b931f4
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/QdUkyWt6cTcdmQXpj6Qe6-s3aYkGfro-G7DYegOVKvA
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
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# About standard and custom states

Five standard player states are available and you can add your own custom states.

|  Standard State Name  |  Media SDK constant                      |  Media Collection API name  |
|-----------------------|------------------------------------------|-----------------------------|
|  Full Screen          |  `ADB.Media.PlayerState.Fullscreen`        |  `fullScreen`                 |
|  Closed Captioning    |  `ADB.Media.PlayerState.ClosedCaptioning`  |  `closedCaptioning`           |
|  Mute                 |  `ADB.Media.PlayerState.Mute`              |  `mute`                       |
|  Picture in Picture   |  `ADB.Media.PlayerState.PictureInPicture`  |  `pictureInPicture`           |
|  In Focus             |  `ADB.Media.PlayerState.InFocus`           |  `inFocus`                    |

The data is computed in the same way for standard and custom states but the data is stored differently for Analytics reporting.

**For standard states**—When you enable the player state tracking from the Media Management console in Analytics reporting (admin side), 15 solution variables are available for reporting and data exports.

**For custom states**—You can create your own processing rules to store the computed values into custom events and then use those rules for reporting and data exports.

## Guidelines

* One video session is limited to 10 player states.
* Any combination of states is allowed.
* If multiple player states pass, only the first 10 are retained and forwarded downstream to the VA processing component.
* The maximum of 10 states is applied for all the states, no matter if they are closed or not.
* A state can start and end multiple times and it is counted as a single state. For example, `closedCapationing` can be started and stopped five times but it will count as a single state.
* Every state that exceeds the maximum of 10 allowed states are discarded.

## Custom states

With the ability to create custom states, you can capture custom actions and update custom metadata during a playback session.

For information about creating custom states, see the [Media API Reference guide: `createStateObject`](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/api-reference/)
