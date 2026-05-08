---
title: Content name (dimension)
description: The Content name dimension reports the human-readable title of each media session.
feature: Dimensions
role: User, Admin
---

# Content name (dimension)

>[!BEGINSHADEBOX]

*This page covers the **Content name (dimension)**. See [Video name (classification)](video-name.md) for the corresponding Adobe Analytics classification derived from the same source value. See [Content name](/help/implementation/variables/core/content-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Content name** dimension reports the human-readable title of each media session. In Adobe Analytics this is the **Content Name (dimension)**; the read-only [Video name (classification)](video-name.md) is automatically derived from the same value and joined to the Content (ID) dimension.

## How this dimension is populated

The friendly name is set by the player at session start. The reported value matches what was sent.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.friendlyName` when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoname` |

>[!IMPORTANT]
>
>If content name is not set, the dimension is unpopulated for that session and the Video Name classification is also unpopulated for that content ID.

## Dimension items

Each item is the literal title reported at session start (for example, `"Blinding Light"`).
