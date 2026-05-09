---
title: Stream format
description: The Stream format dimension reports the quality tier of each session (typically HD or SD).
feature: Dimensions
role: User, Admin
---

# Stream format

>[!BEGINSHADEBOX]

*This page covers the **Stream format** reporting dimension. See [Stream format](/help/implementation/variables/standard-metadata/stream-format.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Stream format** dimension reports the quality tier of each session (typically `"HD"` or `"SD"`, but any string is accepted). Use it to compare engagement, completion, and quality across delivery quality tiers.

## How this dimension is populated

Stream format is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.format` to an eVar. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.streamFormat`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.format` to) |

## Dimension items

Each item is the literal format value reported at session start. Use a stable set of values (`HD`, `SD`, `4K`, `UHD`) so that line items do not fragment across spelling variations.
