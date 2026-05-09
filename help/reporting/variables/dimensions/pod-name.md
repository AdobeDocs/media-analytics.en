---
title: Pod name
description: The Pod name dimension surfaces the friendly name of each ad break as a classification of the Ad pod dimension.
feature: Dimensions
role: User, Admin
---

# Pod name

>[!BEGINSHADEBOX]

*This page covers the **Pod name** reporting dimension. See [Ad break name](/help/implementation/variables/ads/ad-break-name.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Pod name** dimension surfaces the friendly name of each ad break (for example, `"pre-roll"`, `"mid-roll-1"`). In Adobe Analytics it is a classification of the [Ad pod](ad-pod.md) dimension. In Customer Journey Analytics it is a discrete dimension.

## How this dimension is populated

Pod name is auto-populated from the [Ad break name](/help/implementation/variables/ads/ad-break-name.md) value the player sets on `media.adBreakStart`.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Classification of the Ad pod dimension — Adobe automatically populates the classification from the latest `a.media.ad.podFriendlyName` value reported for each ad pod. |
| Customer Journey Analytics | [`mediaReporting.advertisingPodDetails.friendlyName`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-reporting) |
| Data feeds | N/A (Data feeds do not support classifications) |

>[!IMPORTANT]
>
>Do not change the classification name. The classification is automatically created when the report suite is enabled for streaming media reporting. Renaming it can cause Adobe to recreate the original classification.

## Dimension items

Each item is the literal ad break name reported on `media.adBreakStart`.
