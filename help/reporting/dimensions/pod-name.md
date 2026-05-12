---
title: Pod name
description: The Pod name dimension reports the friendly name of each ad break. Collect it in Adobe Analytics using a classification or a custom processing rule.
feature: Dimensions
role: User, Admin
---

# Pod name

>[!BEGINSHADEBOX]

*This page covers the **Pod name** reporting dimension. See [Ad break name](/help/implementation/variables/ads/ad-break-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Pod name** dimension reports the friendly name of each ad break (for example, `"pre-roll"`, `"mid-roll-1"`). In Customer Journey Analytics it is a discrete dimension populated directly from the implementation variable. In Adobe Analytics it is available through two approaches: a classification of the [Ad pod](ad-pod.md) dimension, or an eVar populated using a processing rule.

## How this dimension is populated

Pod name is sourced from the [Ad break name](/help/implementation/variables/ads/ad-break-name.md) value the player sets on `media.adBreakStart`.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics (processing rule) | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.podFriendlyName` to an eVar. |
| Adobe Analytics (classification) | Classification of the Ad pod dimension — Adobe automatically creates this classification when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining classification values. |
| Customer Journey Analytics | [`mediaReporting.advertisingPodDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-reporting) |
| Data feeds (processing rule) | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.ad.podFriendlyName` to) |
| Data feeds (classification) | N/A — Data feeds do not include classification values. |

## Classification approach

Adobe creates the Pod name classification structure automatically when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. You are responsible for populating and maintaining the classification values using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html).

This approach provides a guaranteed 1:1 relationship between each pod ID and its friendly name. Classification updates apply retroactively across all historical data for that ID.

>[!IMPORTANT]
>
>Do not change the Pod name classification name. The classification is automatically created when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Processing rule approach

Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.ad.podFriendlyName` to an eVar. This method captures the friendly name as a per-hit value without requiring classification maintenance.

The trade-off is that you lose the guaranteed 1:1 relationship between the pod name and the parent [Ad pod](ad-pod.md) dimension. If your implementation sends inconsistent values for the same pod ID across events, multiple names can appear under the same ad pod.

## Dimension items

Each item is the literal ad break name reported on `media.adBreakStart`.
