---
title: Controlling the Order of Events
description: Learn about controlling the order of events and how in some cases events are reordered based on the provided timestamp in the playerTime object.
uuid: 007fccc6-be72-4b79-826d-588c957ccf15
exl-id: c0cac319-2bea-42c8-8674-641dfbb44fa2
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/LSKiNN-obuHzVYKbAai52SQ2MvI6-gzgb-G-x0DH2dE
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Controlling the order of events{#controlling-the-order-of-events}

Streaming video tracking is a highly time-dependent operation and occasionally the Media Collection API tracking calls arrive at the back end out-of-order. In this situation, the back end attempts to queue up and reorder events based on the provided timestamp in the `playerTime` object.  This occurs with some limits. Currently, the reorder may fail if the delays between out-of-order calls are more than one second. In future updates, the ‘acceptable delay time’ may be optimized and configurable.

## Out-of-order event example

Out-of-order events occur when events pass through the network which sometimes causes a delay.

For example, you could send an `adBreakStart` event followed by an `adStart` event. This is a common use case, because it's required for an ad to start inside an ad break.

If the ad is ready and no buffer is necessary, both events occur almost instantly and the `playerTime.ts` for both events are very close to each other. However, they should never be equal, since the sorting algorithm wouldn't know what event happened first. Always keep at least a 1-millisecond timestamp difference for any consecutive events.

Because both events occur very close to each other in time when firing network calls, it's possible that they arrive out of order. In this example, the `adStart` event arrives before the `adBreakStart` event.

There is a timed window of events: 5 seconds or a maximum of 10 events. The events are buffered before sending them to the processing pipeline. When the conditions are met (5 seconds have passed or more than 10 events are received), the events are reordered based on the `playerTime.ts` and then sent in the new order to the processing pipeline.

>[!IMPORTANT]
>
>There is an exception event that is sent to the processing pipeline right away and that is the `sessionStart` event.
