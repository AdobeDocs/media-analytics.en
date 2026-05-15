---
title: Session end
description: Immediately close a media session when the viewer abandons content.
feature: Streaming Media
role: Developer
---

# Session end

The session end event immediately and irreversibly closes a media tracking session. Session end is a hard close — once sent, the session is terminated and no further events can be tracked under it. Only use Session end when you are certain that no additional events will follow, such as when the player is destroyed or the page is unloaded. In most cases it is safer to allow the session to expire naturally rather than risk cutting off events that might still arrive. If the viewer finishes the content, call [Session complete](session-complete.md) instead.

Without an explicit session end, a session closes automatically after 10 minutes of no events or 30 minutes of no playhead movement.

* **Prerequisites**: [Session start](session-start.md)
* **Associated metric**: None

## Web SDK

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.sessionEnd"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionEnd",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 45
    }
  }
});
```

## Mobile SDK

Call `trackSessionEnd` when the viewer closes the player or navigates away.

**iOS (Swift)**

```swift
tracker.trackSessionEnd()
```

**Android (Kotlin)**

```kotlin
tracker.trackSessionEnd()
```

## Roku (BrightScript)

Call `sendMediaEvent` with `eventType: "media.sessionEnd"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.sessionEnd",
        "mediaCollection": {
            "playhead": 45
        }
    }
})
```

## Media Edge API

Call the [sessionEnd](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionend) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/sessionEnd?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.sessionEnd",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 45
      },
      "timestamp": "YYYY-08-20T22:41:40+00:00"
    }
  }]
}'
```

## Media SDK

Call `trackSessionEnd` when the viewer closes the player or navigates away:

```javascript
tracker.trackSessionEnd();
```

## Media Collection API

Send a `sessionEnd` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 45, "ts": 1699523820000 },
  "eventType": "sessionEnd"
}
```
