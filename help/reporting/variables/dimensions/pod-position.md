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

The **Pod position** dimension reports the offset of each ad break inside the content, in seconds. A pre-roll has position `0`; mid-rolls have positions corresponding to their playhead start time. In Adobe Analytics the dimension is a classification of the [Ad pod](ad-pod.md) dimension. In Customer Journey Analytics it is a discrete dimension.

## How this dimension is populated

Pod position is auto-populated from the [Ad break start time](/help/implementation/variables/ads/ad-break-start-time.md) value the player sets on `media.adBreakStart`.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Ad pod dimension — Adobe automatically populates the classification from the latest `a.media.ad.podSecond` value reported for each ad pod. |
| Customer Journey Analytics | [`mediaReporting.advertisingPodDetails.offset`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the integer offset value (in seconds) reported on `media.adBreakStart`.
