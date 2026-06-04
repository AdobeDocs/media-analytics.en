---
title: Set up the Media Collection API for streaming media
description: Use the Media Collection API to send streaming media data directly to Adobe Analytics with RESTful HTTP calls.
feature: Streaming Media
role: Developer
---
# Set up the Media Collection API for streaming media

The Media Collection API sends streaming media data directly to Adobe Analytics using RESTful HTTP calls. Because it is fully customizable, it supports custom tracking and devices that the SDKs do not cover. Use it when an SDK is not an option for your platform.

* **Prerequisites**: Complete the [Analytics-only implementation overview](overview.md).

## Implement the API

Open a session with a `sessionStart` request, then send subsequent events to the session it returns. For the complete request/response formats, parameters, validation schemas, and implementation guidance, see the [Media Collection API reference](../media-collection-api/mc-api-overview.md).

## Track media events

See the **Media Collection API** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact payloads.

## Next step

Once your implementation is complete, you can [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

>[!MORELIKETHIS]
>
>* [Media Collection API reference](../media-collection-api/mc-api-overview.md)
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
