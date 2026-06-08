---
title: Ping
description: Send a heartbeat to keep the media session alive and track playback progress at regular intervals.
feature: Streaming Media
role: Developer
---

# Ping

The ping event is a heartbeat that keeps the session alive and tracks playback progress. Send it on a timer throughout playback. On Mobile SDKs, pings are sent automatically; on all other platforms they must be sent manually on the specified interval.

* **Main content**: first ping 10 seconds after playback starts, then every 10 seconds thereafter
* **Ad content**: every 1 second during ad tracking

Do not include a `params` object in the ping request body.

* **Prerequisites**: [Session start](../session/session-start.md)
* **Associated metric**: None

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Schedule a recurring `sendEvent` call with `eventType: "media.ping"`. Update `playhead` to the current playback position on each call:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.ping",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 10
    }
  }
});
```

>[!TAB iOS]

The Mobile SDK sends ping events automatically. No explicit call is required.

>[!TAB Android]

The Mobile SDK sends ping events automatically. No explicit call is required.

>[!TAB Roku Edge]

Schedule a recurring `sendMediaEvent` call with `eventType: "media.ping"`. Update `playhead` to the current playback position on each call:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.ping",
        "mediaCollection": {
            "playhead": 10
        }
    }
})
```

>[!TAB Media Edge API]

Call the [ping](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/ping/) endpoint on a timer. Adobe recommends the first ping 10 seconds after main playback starts, every 10 seconds after that, and every 1 second during ad tracking:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/ping?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.ping",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 10
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

The Media SDK sends ping events automatically. No explicit call is required.

>[!TAB Chromecast]

The Chromecast SDK sends ping events automatically. No explicit call is required.

>[!TAB Roku 2.x]

The Media SDK sends ping events automatically as long as you call `processMediaMessages` in your event loop. Update the playhead so each ping reports the current position:

```brightscript
ADBMobile().mediaUpdatePlayhead(10)
```

>[!TAB Media Collection API]

Send a `ping` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md) on a timer. Do not include a `params` object:

```json
{
  "playerTime": { "playhead": 10, "ts": 1699523820000 },
  "eventType": "ping"
}
```

>[!ENDTABS]
