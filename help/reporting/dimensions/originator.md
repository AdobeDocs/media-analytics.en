---
title: Originator
description: Reports the creator or production studio of the content.
feature: Dimensions
role: User, Admin
---

# Originator

>[!BEGINSHADEBOX]

*This page covers the **Originator** reporting dimension. See [Originator](/help/implementation/variables/standard-metadata/originator.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Originator** dimension reports the creator or production studio of the content (for example, `"Warner Brothers"` or `"Sony"`). Use it to compare engagement across content owners or rights holders.

## How this dimension is populated

Originator is set by the player at session start.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.originator` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Content (ID)](content.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.originator`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.originator` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |
| Audience Manager | `c_contextdata.a.media.originator` |

## Classification approach

Adobe creates the Originator classification structure automatically when **[[!UICONTROL Video Metadata]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each content ID and its originator. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Originator classification name. Renaming it can cause Adobe to recreate the original classification, resulting in a duplicate.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.originator` to an eVar. This approach captures the originator as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the originator and the parent [Content (ID)](content.md) dimension. If your implementation sends inconsistent values for the same content ID across events, multiple originators can appear under the same content. Updating a value only applies to data moving forward.

## Dimension items

Each item is the literal originator value reported at session start. Use a stable, distinct name per studio so engagement does not collapse across unrelated entities.
