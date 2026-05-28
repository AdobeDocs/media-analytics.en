---
seo-title: Overview
title: Streaming Media Collection API Overview
description: Learn about the Media Collection API and how your player can track audio and video events using RESTful HTTP calls.
uuid: c14bdbef-5846-4d31-8a14-8e9e0e9c9861
exl-id: 58430636-7fab-433a-8ead-52ccaa45d920
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/79XLYzuvi3neUuCrt3LcGEwnnaR038-mWHMuSrY797M
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
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
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Media Collection API Overview {#overview}

The Media Collection API is Adobe's RESTful alternative to the client-side Media SDK. With the Media Collection API your player can track audio and video events using RESTful HTTP calls.

The Media Collection API is essentially an adapter, acting as a server-side version of the Media SDK. Collected streaming media tracking data leads to the same [Reporting and Analysis](/help/implementation/media-sdk/setup/media-reports-enable.md).

## Media Tracking Data Flows {#media-tracking-data-flows}

A media player implementing the Media Collection API makes RESTful API tracking calls directly to the media tracking back-end server, whereas a player implementing the Media SDK makes tracking calls to the SDK APIs inside the player app. One effect of making calls over the web is that the player implementing the Media Collection API needs to handle some of the processing that the Media SDK handles automatically. (Details in [Media Collection Implementation.](mc-api-impl/mc-api-quick-start.md))

The tracking data captured with the Media Collection API is sent and initially processed differently than the tracking data captured in a Media SDK player, but the same processing engine on the back-end is used for both solutions.

![](assets/col_api_overview_simple.png)

## API Overview {#api-overview}

**URI:** Obtain this from your Adobe representative.

**HTTP Method:** POST, with JSON request body.

### API Calls {#mc-api-calls}

* **`sessions` -** Establishes a session with the server, and returns a Session ID used in subsequent `events` calls. Your app calls this once at the start of a tracking session.

  `{uri}/api/v1/sessions`

* **`events` -** Sends media tracking data.

  `{uri}/api/v1/sessions/{session-id}/events`

### Request Body {#mc-api-request-body}

```json
{
    "playerTime": {
        "playhead": "{playhead position in seconds}",
        "ts": "{timestamp in milliseconds}"
    },
    "eventType": "{event-type}",
    "params": {
        "{parameter-name}": "{parameter-value}",
        "{parameter-name}": "{parameter-value}"
    },
    "qoeData" : {
        "{parameter-name}": "{parameter-value}",
        "{parameter-name}": "{parameter-value}"
    },
    "customMetadata": {
        "{parameter-name}": "{parameter-value}",
        "{parameter-name}": "{parameter-value}"
    }
}
```

* `playerTime` - Mandatory for all requests.
* `eventType` - Mandatory for all requests.
* `params` - Mandatory for certain `eventTypes`; check the [JSON validation schema](mc-api-ref/mc-api-json-validation.md) to determine which eventTypes are mandatory, and which are optional.

* `qoeData` - Optional for all requests.
* `customMetadata` - Optional for all requests, but only sent with `sessionStart`, `adStart`, and `chapterStart` event types.

For each `eventType`, there is a publicly available [JSON validation schema](mc-api-ref/mc-api-json-validation.md) that you should use to verify parameter types and whether a parameter is optional or required for a particular event.

### Event Types {#mc-api-event-types}

For the full list of event types with per-SDK implementation examples, see the [Events overview](/help/implementation/events/overview.md).
