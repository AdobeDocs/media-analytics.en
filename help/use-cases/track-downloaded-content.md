---
title: How to track offline downloaded content in streaming media services
description: Learn how to use the Downloaded Content feature to track media consumption when a user is offline.
uuid: 0718689d-9602-4e3f-833c-8297aae1d909
exl-id: 82d3e5d7-4f88-425c-8bdb-e9101fc1db92
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/rtLBRcyLB8D8HPBj-Qw5LD824Fu8KeUDsLokJCn2Wfc
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: e992d880-33bc-4949-a648-aa7d410276cd
    internal-label: Validation
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
# Track downloaded content{#track-downloaded-content}

## Overview {#overview}

The Downloaded Content feature provides the ability to track media consumption while a user is offline. For example, a user downloads and installs an app on a mobile device then uses the app to download content into local storage on the device. To track the downloaded data, Adobe developed the Downloaded Content feature. With this feature, when the user plays content from a device's storage, tracking data is stored on the device regardless of the device's connectivity. When the user finishes the playback session and the device returns online, the stored tracking information is sent to the Media Collection API back-end inside a single payload. The stored tracking information is then processed and reported as usual in the Media Collection API.

Contrast the two approaches:

* Online

   With this real-time approach, the media player sends tracking data for each player event, and it sends network pings every ten seconds (every one second for ads), one by one to the back-end.

* Offline (Downloaded Content feature)

   With this batch-processing approach, the same session events need to be generated, but they are stored on the device until they are sent to the back-end as a single session (see example below).

Each approach has its advantages and disadvantages:
* The online scenario tracks in realtime; this requires a connectivity check before each network call.
* The offline scenario (Downloaded Content feature) only needs one network connectivity check, but also requires a larger memory footprint on the device.

## Implementation {#implementation}

### Supported platforms

Content tracking is supported on iOS and Android mobile devices.

### Event schemas

The Downloaded Content feature is the offline version of the the (standard) online Media Collection API, so the event data that your player batches and sends to the back-end must use the same event schemas that you use when you make online calls. For information on these schemas, see:
* [Overview;](/help/implementation/media-collection-api/mc-api-overview.md)
* [Validating event requests](/help/implementation/media-collection-api/mc-api-impl/mc-api-validate-reqs.md)

### Order of events

* The first event in the batch payload must be `sessionStart` as per usual with the Media Collection API.
* **You must include `media.downloaded: true`** in the standard metadata parameters (`params` key) on the `sessionStart` event to indicate to the back-end that you are sending downloaded content. If this parameter is not present or is set to false when you send downloaded data, the API will return a 400 response code (Bad Request). This parameter distinguishes downloaded versus live content to the back-end. If `media.downloaded: true` is set on a live session, this will likewise result in a 400 response from the API.
* It is the responsibility of the implementation to correctly store player events in the order of their appearance.

### Response codes

* 201 - Created: Successful Request; the data is valid and the session was created and will be processed.
* 400 - Bad Request; schema validation has failed, all data is discarded, no sessions data will be processed.

## Integration with Adobe Analtyics {#integration-with-adobe-analtyics}

When computing the Analytics start/close calls for the downloaded content scenario, the back-end sets an extra Analytics field called `ts.` These are timestamps for the first and last events received (start and complete). This mechanism allows a completed media session to be placed at the correct point in time (i.e., even if the user doesn't come back online for several days, the media session is reported to have occurred at the time the content was actually viewed). You must enable this mechanism on the Adobe Analytics side by creating a _timestamp optional report suite._ To enable a timestamp optional report suite, see [Timestamps Optional.](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/timestamp-optional.html)

## Sample session comparison {#sample-session-comparison}

### Online Content

```
POST /api/v1/sessions HTTP/1.1

{
  eventType: "sessionStart",
  playerTime: {
    playhead: 0,  
    ts: 1529997923478},  
  params: { /* Standard metadata parameters as documented */ },  
  customMetadata: { /* Custom metadata parameters as documented */ },  
  qoeData: { /* QoE parameters as documented */ }
}
```

### Downloaded Content

```
POST /api/v1/downloaded HTTP/1.1

[{
    eventType: "sessionStart",
    playerTime:{
      playhead: 0,
      ts: 1529997923478
    },  
    params:{...},
    customMetadata:{},  
    qoeData:{}
},
    {eventType: "play", playerTime:
        {playhead: 0,  ts: 1529997928174}},
    {eventType: "ping", playerTime:
        {playhead: 10, ts: 1529997937503}},
    {eventType: "ping", playerTime:
        {playhead: 20, ts: 1529997947533}},
    {eventType: "ping", playerTime:
        {playhead: 30, ts: 1529997957545},},
    {eventType: "sessionComplete", playerTime:
        {playhead: 35, ts: 1529997960559}
}]
```

### Deprecation Notice

>[!IMPORTANT]
>
>Downloaded content could previously also be sent to `/api/v1/sessions` API. This way of tracking downloaded content is **deprecated** and will be **removed** in the future.


The `/api/v1/sessions` API will only accept session initialization events.
When using the new API, the previously mandatory `media.downloaded` flag is no longer necessary.
We strongly suggest using the `/api/v1/downloaded` API for new downloaded content implementations, as well as updating existing implementations that rely on the old API.  


```
POST /api/v1/sessions HTTP/1.1
[{
    eventType: "sessionStart",
    playerTime:{
      playhead: 0,
      ts: 1529997923478
    },
    params:{
        "media.downloaded": true,
        ...
    },
    customMetadata:{},  
    qoeData:{}
},
    {eventType: "play", playerTime:
        {playhead: 0,  ts: 1529997928174}},
    {eventType: "ping", playerTime:
        {playhead: 10, ts: 1529997937503}},
    {eventType: "ping", playerTime:
        {playhead: 20, ts: 1529997947533}},
    {eventType: "ping", playerTime:
        {playhead: 30, ts: 1529997957545},},
    {eventType: "sessionComplete", playerTime:
        {playhead: 35, ts: 1529997960559}
}]

```

## Media tracker API reference

For information about how to configure downloaded content, see the [Media tracker API reference](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/api-reference/).
