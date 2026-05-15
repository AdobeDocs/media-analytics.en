---
title: Content type
description: Reports the format of the stream (VOD, Live, Linear, podcast, song, and so on).
feature: Dimensions
role: User, Admin
---

# Content type

>[!BEGINSHADEBOX]

*This page covers the **Content type** reporting dimension. See [Content type](/help/implementation/variables/core/content-type.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content type** dimension reports the format of the stream (for example, VOD, Live, or Linear for video, and song, podcast, or audiobook for audio).

## How this dimension is populated

Content type is set by the player at session start and carried through every event. It is not derived; the value reported matches what was sent during collection.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.contentType` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.contentType`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videocontenttype`, `post_videocontenttype` |
| Audience Manager | `c_contextdata.a.contentType` |

>[!IMPORTANT]
>
>If content type is not set or is empty, the dimension reports `missing_content_type` for the session. Use this value to find implementations that need to be fixed.

## Dimension items

Adobe-defined values populate the built-in segments and reports. Custom strings are accepted but will not match the built-in segments.

| Stream type | Recommended values |
| --- | --- |
| Video | `vod`, `live`, `linear`, `ugc`, `dvod` |
| Audio | `song`, `podcast`, `audiobook`, `radio` |

## Recommended segments

| Segment | Rule |
| --- | --- |
| [!UICONTROL VOD content] | Content Type = `vod` |
| [!UICONTROL Live content] | Content Type = `live` |
| [!UICONTROL Linear content] | Content Type = `linear` |
