---
title: Content name
description: The Content name dimension reports the human-readable title of each media session.
feature: Dimensions
role: User, Admin
---

# Content name

>[!BEGINSHADEBOX]

*This page covers the **Content name** reporting dimension. See [Content name](/help/implementation/variables/core/content-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content name** dimension reports the human-readable title of each media session.

## How this dimension is populated

The friendly name is set by the player at session start. The reported value matches what was sent.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.friendlyName` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoname, post_videoname` |

>[!NOTE]
>
>In Adobe Analytics, this value also automatically populates a **Video name** classification on the [Content](content.md) dimension from the same source value. Customer Journey Analytics uses this dimension directly. Use whichever component that your implementation workflow best supports.

>[!IMPORTANT]
>
>If content name is not set, the dimension is unpopulated for that session.

## Dimension items

Each item is the literal title reported at session start (for example, `"Blinding Light"`).
