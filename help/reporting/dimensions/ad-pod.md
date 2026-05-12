---
title: Ad pod
description: Reports each unique ad break, keyed by an auto-generated pod ID.
feature: Dimensions
role: User, Admin
---

# Ad pod

The **Ad pod** dimension reports each unique ad break, keyed by an auto-generated pod ID. Every ad in a session belongs to a parent ad pod, and the pod groups multiple ads played back-to-back. Use the dimension to break out engagement by ad break and as the join key for the [Pod name](pod-name.md) and [Pod position](pod-position.md) classifications.

## How this dimension is populated

The ad pod ID is generated automatically by the SDK when `media.adBreakStart` fires. Direct API implementations construct it from the break index and start time, or supply a custom pod ID.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.ad.pod` when [[!UICONTROL Media Ads]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.advertisingPodDetails.ID`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/advertising-pod-details-reporting) |
| Data feeds | `videoadpod, post_videoadpod` |

## Dimension items

Each item is a unique ad pod ID. The ID is opaque (typically a hash of session ID, content ID, and break index) and is most useful as a grouping key when combined with [Pod name](pod-name.md) for the friendly label.
