---
title: Set up the Media Edge API for streaming media
description: Send streaming media data directly to the Edge Network using the Media Edge API.
feature: Streaming Media
role: Developer
---
# Set up the Media Edge API for streaming media

If you cannot use the Web SDK, Mobile SDK, or Roku SDK — for example, on a custom or unsupported runtime — you can send streaming media data directly to the Edge Network with the Media Edge API. The API uses RESTful HTTP calls and is fully customizable.

* **Prerequisites**: Complete the [Edge implementation overview](overview.md) (schema, dataset, datastream with [!UICONTROL Media Analytics] enabled).

## Send media events to the Edge Network

Media events are sent to the `/ee/va/v1/` endpoints, keyed to your datastream by the `configId` query parameter. For example, a session starts with a POST to `sessionStart`:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/sessionStart?configId=<datastreamID>" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.sessionStart",
      "mediaCollection": {
        "sessionDetails": { "name": "video-123", "playerName": "player_name", "contentType": "vod", "length": 128, "channel": "sample_channel" },
        "playhead": 0
      }
    }
  }]
}'
```

The response returns the session ID that all subsequent events must include. For the full endpoint set, request/response formats, and the OpenAPI specification, see the [Media Edge API reference](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/).

## Track media events

See the **Media Edge API** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact payloads.

## Next step

Once your implementation is complete, you can [Set up reporting for Edge implementations](/help/reporting/setup/edge-reporting.md).

>[!MORELIKETHIS]
>
>* [Media Edge API reference](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/)
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
