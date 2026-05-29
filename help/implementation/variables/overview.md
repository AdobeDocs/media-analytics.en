---
title: Streaming media variables overview
description: Learn how streaming media variables are organized and how they map across Adobe Analytics and Customer Journey Analytics.
feature: Streaming Media
role: User, Admin, Developer
---

# Streaming media variables overview

Variables are the data that your media player supplies about a stream, such as content name, stream type, ad name, and playback quality. Most variables are set at session start and carried through to session close by the media backend, which uses them to populate the dimensions and metrics that you use in reporting. Each variable page documents how to set that variable across every supported implementation method.

## How variables are sent to Adobe

A single variable carries the same value to every Adobe application or service, but the format of that value depends on where you send it. The following table lists each application or service and the variable format that it expects. The properties table on each variable page shows the exact value to use in every format.

| Data format | Description |
| --- | --- |
| Context data variable | The format sent to Adobe Analytics, named with an `a.media` prefix (such as `a.media.name`). |
| XDM collection field | The format sent to Customer Journey Analytics, expressed as an XDM field path (such as `xdm.mediaCollection.sessionDetails.name`). |
| Audience Manager trait | The format forwarded to Audience Manager, prefixed with `c_contextdata` (such as `c_contextdata.a.media.name`). |

>[!MORELIKETHIS]
>
>* [Events overview](/help/implementation/events/overview.md): The player events that carry variables
>* [Dimensions overview](/help/reporting/dimensions/overview.md): The reporting dimensions that variables populate
>* [Metrics overview](/help/reporting/metrics/overview.md): The reporting metrics that variables populate
