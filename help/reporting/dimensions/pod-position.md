---
title: Pod position
description: Reports the offset of each ad break inside the content.
feature: Dimensions
role: User, Admin
---

# Pod position

>[!BEGINSHADEBOX]

*This page covers the **Pod position** reporting dimension. See [Ad break start time](/help/implementation/variables/ads/ad-break-start-time.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Pod position** dimension reports the offset of each ad break inside the content, in seconds. A pre-roll has position `0`; mid-rolls have positions corresponding to their playhead start time.

## How this dimension is populated

Pod position is set from the [Ad break start time](/help/implementation/variables/ads/ad-break-start-time.md) value the player sets on `media.adBreakStart`.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.podSecond` to an eVar. |
| Adobe Analytics (classification) | Classification of the [Ad pod](ad-pod.md) dimension — Adobe automatically creates this classification when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.advertisingPodDetails.offset`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.ad.podSecond` to) |
| Data feeds (classification) | N/A — Data feeds do not support classifications. |

## Classification approach

Adobe creates the Pod position classification structure automatically when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each ad pod ID and its position. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Pod position classification name. Renaming it can cause Adobe to recreate the original classification, resulting in a duplicate.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.podSecond` to an eVar. This approach captures the pod position as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the pod position and the parent [Ad pod](ad-pod.md) dimension. If your implementation sends inconsistent values for the same pod ID across events, multiple positions can appear under the same ad pod. Updating a value only applies to data moving forward.

## Dimension items

Each item is the integer offset value (in seconds) reported on `media.adBreakStart`.
