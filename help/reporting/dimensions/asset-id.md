---
title: Asset ID
description: Reports a stable industry identifier for the underlying media asset.
feature: Dimensions
role: User, Admin
---

# Asset ID

>[!BEGINSHADEBOX]

*This page covers the **Asset ID** reporting dimension. See [Asset ID](/help/implementation/variables/standard-metadata/asset-id.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Asset ID** dimension reports a stable industry identifier for the underlying media asset (typically an EIDR, TMS/Gracenote, or Rovi ID, but proprietary IDs are also accepted).

## How this dimension is populated

Asset ID is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.asset` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Content (ID)](content.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.assetID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.asset` to) |
| Data feeds (classification) | N/A — Data feeds do not include classification values. |

## Classification approach

Adobe creates the Asset ID classification structure automatically when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification values using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each content ID and its asset ID. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Asset ID classification name. The classification is automatically created when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.asset` to an eVar. This method captures the asset ID as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the asset ID and the parent [Content (ID)](content.md) dimension. If your implementation sends inconsistent values for the same content ID across events, multiple asset IDs can appear under the same content.

## Dimension items

Each item is a unique asset ID value reported during the report period. Use a single stable identifier per asset across all distribution platforms so the same content rolls up to a single line item.
