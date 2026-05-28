---
title: Track Ads
description: Overview of implementing ad tracking with the Media SDK.
uuid: 1607798b-c6ef-4d60-8e40-e958c345b09c
exl-id: c714d31f-3d08-4ded-a413-2762d53bec75
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/PguxKIzAL95WbMl5c0yJq9rYSqZgOGbbAYtxOI4eVOs
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---

# Track ads

Ad playback tracking covers ad breaks, ad starts, ad completes, and ad skips. Use the media player's API to identify key player events and populate the required ad variables.

## Player events

| Player event | Action |
| --- | --- |
| Ad break start | Create ad break object; call AdBreakStart |
| Ad start | Create ad object; call AdStart |
| Ad complete | Call AdComplete |
| Ad skip | Call AdSkip |
| Ad break complete | Call AdBreakComplete |

## Implementation steps

1. Identify when the ad break boundary begins, including pre-roll, and create an ad break object. See [Ad break name](/help/implementation/variables/ads/ad-break-name.md) and [Ad break start time](/help/implementation/variables/ads/ad-break-start-time.md) for field definitions.
1. Call [Ad break start](/help/implementation/events/ads/ad-break-start.md) to begin tracking the ad break.
1. Identify when the ad starts and create an ad object. See [Ad name](/help/implementation/variables/ads/ad-name.md), [Ad ID](/help/implementation/variables/ads/ad-id.md), [Ad length](/help/implementation/variables/ads/ad-length.md), [Ad in pod position](/help/implementation/variables/ads/ad-in-pod-position.md), and [Ad player name](/help/implementation/variables/ads/ad-player-name.md) for field definitions.
1. Optionally attach standard ad metadata. See [Advertiser](/help/implementation/variables/ads/advertiser.md), [Campaign ID](/help/implementation/variables/ads/campaign-id.md), [Creative ID](/help/implementation/variables/ads/creative-id.md), [Creative URL](/help/implementation/variables/ads/creative-url.md), [Placement ID](/help/implementation/variables/ads/placement-id.md), and [Site ID](/help/implementation/variables/ads/site-id.md) for available keys.
1. Call [Ad start](/help/implementation/events/ads/ad-start.md) to begin tracking the ad.
1. When the ad plays to completion, call [Ad complete](/help/implementation/events/ads/ad-complete.md).
1. If the viewer skipped the ad, call [Ad skip](/help/implementation/events/ads/ad-skip.md) instead of Ad complete.
1. For additional ads in the same ad break, repeat steps 3 through 7.
1. When the ad break is complete, call [Ad break complete](/help/implementation/events/ads/ad-break-complete.md).

>[!IMPORTANT]
>
>**Pre-roll ads: do not call `trackPlay` before `AdBreakStart` and `AdStart`.** The first `play` ping on main content increments [Content starts](/help/reporting/metrics/content-starts.md). If `trackPlay` is called before the pre-roll ad events fire and the viewer drops out during the ad, Content starts is incremented even though no main content was ever played. For pre-roll scenarios, delay `trackPlay` until after `AdBreakStart` and `AdStart` have been sent.

>[!NOTE]
>
>The playhead value reported during ad playback represents the viewer's position within the **main content**, not within the ad. For a pre-roll ad preceding a 10-minute video, the playhead is `0` throughout the entire ad. For a mid-roll ad that starts at the 5-minute mark, the playhead remains at `300` (seconds) for the duration of the ad.

## Common issues

### Unexpected main:play calls between ads

If you see `main:play` calls occurring between consecutive ads, a gap of more than 250 milliseconds exists between the AdComplete call and the next AdStart call. When this gap occurs the Media SDK falls back to sending main content pings, which can set the Content starts metric early for pre-roll scenarios.

**Cause:** The Media SDK has no ad information set and the player is in a playing state, so it credits the gap duration to main content.

**Resolution:** Delay the AdComplete call for each ad (except the last) rather than calling it immediately when the ad ends. Batch the calls as follows:

- On every **ad start**: If a previous ad exists and was not yet marked complete, call AdComplete *before* calling AdStart for the new ad.
- On every **ad asset end**: Do not call AdComplete immediately — defer it.
- On **ad break complete**: Call AdComplete for the last ad (if not already called), then call AdBreakComplete.

This pattern ensures that AdComplete and the next AdStart fire back-to-back, eliminating any gap.
