---
title: Publisher
description: Reports the audio content publisher.
feature: Dimensions
role: User, Admin
---

# Publisher

>[!BEGINSHADEBOX]

*This page covers the **Publisher** reporting dimension. See [Publisher](/help/implementation/variables/standard-metadata/publisher.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Publisher** dimension reports the audio content publisher (for example, a podcast network or audiobook publisher). Use it to compare engagement across publishers in a curated audio catalog.

## How this dimension is populated

Publisher is set by the player at session start for audio content.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.publisher` when [[!UICONTROL Audio Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.publisher`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoaudiopublisher` |

## Dimension items

Each item is the literal publisher name reported at session start.
