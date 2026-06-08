---
title: Ad loads
description: Reports the type of ad load used for each streaming media session.
feature: Dimensions
role: User, Admin
---

# Ad loads

>[!BEGINSHADEBOX]

*This page covers the **Ad loads** reporting dimension. See [Ad load type](/help/implementation/variables/standard-metadata/ad-load-type.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Ad loads** dimension reports the type of ad loaded at the start of each streaming media session. The value is customer-defined, allowing organizations to classify sessions by their ad delivery mechanism (for example, `"linear"`, `"dynamic"`, or `"programmatic"`).

## How this dimension is populated

Ad load type is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.adLoad` when [[!UICONTROL Streaming Media]](/help/reporting/setup/analytics-reporting.md) is configured. |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.adLoad`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `videoadload`, `post_videoadload` |
| Audience Manager | `c_contextdata.a.media.adLoad` |

## Dimension items

Each item is the literal ad load type string set at session start. Values are not constrained to a standard enumeration. Define a taxonomy that is consistent across your implementations so values roll up predictably in reports.
