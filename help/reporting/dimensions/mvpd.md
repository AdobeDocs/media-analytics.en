---
title: MVPD
description: Reports the cable, satellite, or virtual provider through which the user authenticated.
feature: Dimensions
role: User, Admin
---

# MVPD

>[!BEGINSHADEBOX]

*This page covers the **MVPD** reporting dimension. See [MVPD](/help/implementation/variables/standard-metadata/mvpd.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **MVPD** (multichannel video programming distributor) dimension reports the provider through which the user authenticated via Adobe Pass (for example, `"Comcast"` or `"DirecTV"`). Use it to break out engagement by authentication provider.

## How this dimension is populated

MVPD is set by the player at session start when the content is gated behind Adobe Pass.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.pass.mvpd` when [[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.mvpd`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videomvpd`, `post_videomvpd` |
| Audience Manager | `c_contextdata.a.media.pass.mvpd` |

## Dimension items

Each item is the literal MVPD name reported at session start. Use the canonical Adobe Pass MVPD identifier per provider so data rolls up to a single line item per provider.
