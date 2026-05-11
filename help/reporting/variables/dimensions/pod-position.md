---
title: Pod position
description: The Pod position dimension reports the offset of each ad break inside the content as a classification of the Ad pod dimension.
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
| Adobe Analytics | Classification of the [Ad pod](ad-pod.md) dimension, created when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingPodDetails.offset`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

In Adobe Analytics, this dimension is a classification of the [Ad pod](ad-pod.md) dimension. Adobe creates the classification when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled, but populating and maintaining the values is your responsibility using [Classification sets](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/overview.html). If you prefer not to manage a classification, use the [Ad break start time](/help/implementation/variables/ads/ad-break-start-time.md) implementation variable directly on every relevant event; this method requires no classification maintenance, but you lose the guaranteed 1:1 relationship between this value and the parent [Ad pod](ad-pod.md) dimension.

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when **[[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md)** is enabled for the report suite. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the integer offset value (in seconds) reported on `media.adBreakStart`.
