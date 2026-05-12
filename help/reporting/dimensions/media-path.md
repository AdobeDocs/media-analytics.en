---
title: Media path
description: Captures the content ID as a traffic variable for path analysis.
feature: Dimensions
role: User, Admin
---

# Media path

The **Media path** dimension captures the content ID as a traffic variable (prop) so it can be used in pathing analysis (for example, the next-content and previous-content flow reports). It is unique to Adobe Analytics: Customer Journey Analytics does not store traffic variables, and pathing is performed on the Content (ID) dimension directly.

## How this dimension is populated

Media path is automatically derived from the content ID set at session start. There is no separate variable to set; the data feed column `videopath` is populated whenever Content (ID) is populated.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.name` as a traffic variable (prop) when [[!UICONTROL Media Core]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | N/A — use [Content](content.md) for path analysis |
| Data feeds | `videopath, post_videopath` |

>[!IMPORTANT]
>
>Pathing reports compare the prop value across hits within the same visit. If Content (ID) changes within a visit (for example, when a viewer moves from one piece of content to another), the path report shows that flow.

## Dimension items

Each item is a content ID reported during a visit. Use the Next Page Flow and Previous Page Flow reports under Content > Media path in Adobe Analytics to view content-to-content navigation paths.
