---
title: Content name
description: Reports the human-readable title of each media session.
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
| Adobe Analytics | Automatically collected from context data `a.media.friendlyName` when [[!UICONTROL Media Core]](/help/reporting/setup/analytics-reporting.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoname`, `post_videoname` |
| Audience Manager | `c_contextdata.a.media.friendlyName` |

>[!NOTE]
>
>In Adobe Analytics, this value also corresponds to a **Video name** classification on the [Content](content.md) dimension. You are responsible for populating and maintaining that classification separately. Customer Journey Analytics uses this dimension directly.

>[!IMPORTANT]
>
>If content name is not set, the dimension is unpopulated for that session.

## Dimension items

Each item is the literal title reported at session start (for example, `"Blinding Light"`).
