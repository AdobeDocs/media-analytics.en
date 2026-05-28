---
title: Content
description: Reports each unique piece of media played, keyed by the content ID.
feature: Dimensions
role: User, Admin
---

# Content

>[!BEGINSHADEBOX]

*This page covers the **Content** reporting dimension. See [Content ID](/help/implementation/variables/core/content-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content** dimension reports each unique piece of media played, keyed by the content ID set at session start. It is the primary breakdown for streaming media reporting and the join key for classification dimensions such as Video Name, Video Length, Asset ID, First Air Date, and Content Rating.

## How this dimension is populated

Content is set by the player at session start as a stable identifier for the asset. The same content ID is reported on every subsequent event for the session.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.name` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. Persists for the duration of the visit. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.name`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `video`, `post_video` |
| Audience Manager | `c_contextdata.a.media.name` |

>[!IMPORTANT]
>
>Content ID is required. If it is unset or empty, the session is dropped from streaming media reporting and will not appear in any media report or in the [!UICONTROL All streaming media] segment.

## Dimension items

Each item is a unique content ID reported at session start. Use a stable identifier (for example, an internal CMS ID, an industry ID such as EIDR or TMS/Gracenote, or a persistent slug) so that sessions for the same asset roll up to a single line item over time.

## Recommended segments

| Segment | Rule |
| --- | --- |
| [!UICONTROL All streaming media] | Content (ID) exists |
