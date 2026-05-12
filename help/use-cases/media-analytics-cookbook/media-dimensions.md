---
title: What is Media Stream Attribution?
description: Learn how to link application actions to media tracking data without the need for additional processing rules and custom variables.
exl-id: 75cc9088-776d-4b10-b358-9fff956a7eb7
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/G0RufpSDBB65tr4XJRvPU2keKgKxv1uDviyhqzxEVD4
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e4f5f438-eabb-4c54-9133-b817e3d125f5
    internal-label: Use cases
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
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
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Media Stream Attribution {#media-stream-attribution}

With Media Stream Attribution, you can link application actions to media tracking data without the need for additional processing rules and custom variables.

## Media Dimensions Outside Media Tracking

You can add media dimensions to analytics calls such as page views and custom links. During implementation, you must add the media context data parameters to the Analytics track calls.

To enable this feature for a specific report, re-enable the media tracking configuration from the Admin console.

>[!NOTE]
>
>The media metrics are _not_ available for use outside of media tracking because most of these are computed by the streaming media services based on heartbeat events. Also, it is important that the media metrics not be inflated by different implementations.

## Using Media Stream Attribution

The JavaScript example below generates a Custom Link tracking call that has the name set to "Hero Banner".

```javascript
s.contextData["a.media.show"]="Mi Amore"
s.tl(this,'o','Hero Banner');
```

In Analytics reporting, you can use the `Show` eVar to break down the data, and you will be able to count the track link instances. The reporting would look similar to this:

![](/assets/myShow-rpt-1.png)

## Use Cases

The following examples show use cases for the following:

* Category Placement
* Hero Placement
* Engagement
* Subscriptions

![](/assets/vid-stream-attr-category.png)

![](/assets/vid-stream-attr-hero.png)

![](/assets/show-engagement.png)

![](/assets/vid-stream-attr-subs.png)
