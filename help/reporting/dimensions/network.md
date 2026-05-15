---
title: Network
description: Reports the broadcast network or channel name.
feature: Dimensions
role: User, Admin
---

# Network

>[!BEGINSHADEBOX]

*This page covers the **Network** reporting dimension. See [Network](/help/implementation/variables/standard-metadata/network.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Network** dimension reports the broadcast network or channel name (for example, `"Fox"` or `"ESPN"`). Use it to compare engagement across networks within the same streaming property.

## How this dimension is populated

Network is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.network` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.network`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videonetwork`, `post_videonetwork` |
| Audience Manager | `c_contextdata.a.media.network` |

## Dimension items

Each item is the literal network value reported at session start. Use a stable, distinct name per network so data does not fragment across spelling variants.
