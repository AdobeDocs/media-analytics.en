---
title: Stream type
description: Captures whether each media session was audio or video content.
feature: Dimensions
role: User, Admin
---

# Stream type

>[!BEGINSHADEBOX]

*This page covers the **Stream type** reporting dimension. See [Stream type](/help/implementation/variables/core/stream-type.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Stream type** dimension captures whether each media session was audio or video content. It is available in Adobe Analytics once [Media Core is enabled](/help/implementation/media-sdk/setup/media-reports-enable.md) for the report suite, and in Customer Journey Analytics for any dataset that includes streaming media data.

## How this dimension is populated

Stream type is set by the player at session start and carried through to the session close call. It is not computed or derived. The value reported exactly matches what was sent during collection.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.streamType` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.streamType`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videostreamtype` |
| Audience Manager | `c_contextdata.a.media.streamType` |

>[!IMPORTANT]
>
>If stream type is not set, the dimension is unpopulated for that session. Those sessions are excluded from the built-in Audio only and Video only segments, and the All streaming media segment will undercount if used in conjunction with stream type breakdowns.

## Dimension items

| Value | Description |
| --- | --- |
| `video` | The session was video content. |
| `audio` | The session was audio content such as a podcast, audiobook, or music stream. |

Custom values are technically accepted by the collection APIs but are not recommended. They will not match the built-in segments described below and may cause inconsistent reporting across implementations.

## Recommended segments

Stream type is the basis for Adobe Analytics' built-in [!UICONTROL Media Stream Type] segments. Use these segments to scope any streaming media report to a specific content type:

| Segment | Rule |
| --- | --- |
| [!UICONTROL All streaming media] | Content (ID) exists |
| [!UICONTROL Audio only] | Content (ID) exists AND Stream Type = `audio` |
| [!UICONTROL Video only] | Content (ID) exists AND Stream Type != `audio` |

>[!TIP]
>
>The [!UICONTROL Video only] segment uses a `!=` rule rather than `= video` to correctly capture sessions where stream type may have been set to a custom value that is not `audio`.
