---
title: Placement ID
description: The Placement ID dimension reports the placement identifier for each ad.
feature: Dimensions
role: User, Admin
---

# Placement ID

>[!BEGINSHADEBOX]

*This page covers the **Placement ID** reporting dimension. See [Placement ID](/help/implementation/variables/ads/placement-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Placement ID** dimension reports the ad placement identifier (typically a slot or zone defined in your ad-server platform). Use the dimension to compare engagement and completion across placement slots.

## How this dimension is populated

Placement ID is set by the player on every `media.adStart` event.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.placement` to an eVar. |
| Customer Journey Analytics | [`mediaReporting.advertisingDetails.placementID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-details-reporting) |
| Data feeds | N/A |

## Dimension items

Each item is the literal placement value reported on `media.adStart`.
