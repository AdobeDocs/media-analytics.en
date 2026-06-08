---
title: Buffer start
description: Signal that the media player entered a buffering state.
feature: Streaming Media
role: Developer
---

# Buffer start

The buffer start event signals that the media player entered a buffering state.

* **Prerequisites**: [Session start](../session/session-start.md)
* **Associated metric**: [[!UICONTROL Buffer events]](/help/reporting/metrics/buffer-events.md)

>[!NOTE]
>
>**XDM-based APIs (Web SDK, Roku, Media Edge API, Media Collection API):** There is no buffer resume event type; buffer end is inferred when you send a [`play`](play.md) event after `bufferStart`.
>
>**Mobile SDK:** Call `trackEvent(BufferComplete)` when the player exits buffering, then call `trackPlay()` to resume playback.

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Call [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview) with `eventType: "media.bufferStart"`:

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.bufferStart",
    mediaCollection: {
      sessionID: "{sid}",
      playhead: 45
    }
  }
});
```

>[!TAB iOS]

Call `trackEvent` with `BufferStart` when the player enters a buffering state, and `BufferComplete` when it exits.

```swift
// Buffer starts
tracker.trackEvent(event: MediaEvent.BufferStart, info: nil, metadata: nil)

// Buffer ends
tracker.trackEvent(event: MediaEvent.BufferComplete, info: nil, metadata: nil)
```

>[!TAB Android]

Call `trackEvent` with `BufferStart` when the player enters a buffering state, and `BufferComplete` when it exits.

```kotlin
// Buffer starts
tracker.trackEvent(Media.Event.BufferStart, null, null)

// Buffer ends
tracker.trackEvent(Media.Event.BufferComplete, null, null)
```

>[!TAB Roku Edge]

Call `sendMediaEvent` with `eventType: "media.bufferStart"`:

```brightscript
m.aepSdk.sendMediaEvent({
    "xdm": {
        "eventType": "media.bufferStart",
        "mediaCollection": {
            "playhead": 45
        }
    }
})
```

>[!TAB Media Edge API]

Call the [bufferStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/bufferstart/) endpoint:

```sh
curl -X POST "https://edge.adobedc.net/ee/va/v1/bufferStart?configId={datastreamID}" \
--header 'Content-Type: application/json' \
--data '{
  "events": [{
    "xdm": {
      "eventType": "media.bufferStart",
      "mediaCollection": {
        "sessionID": "{sid}",
        "playhead": 45
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

Call `trackEvent` with the `BufferStart` event type:

```javascript
tracker.trackEvent(ADB.Media.Event.BufferStart, null, null);
```

>[!TAB Chromecast]

Call `trackEvent` with `BufferStart` when the player enters a buffering state, and `BufferComplete` when it exits:

```javascript
// Buffer starts
ADBMobile.media.trackEvent(ADBMobile.media.Event.BufferStart);

// Buffer ends
ADBMobile.media.trackEvent(ADBMobile.media.Event.BufferComplete);
```

>[!TAB Roku 2.x]

Call `mediaTrackEvent` with `MEDIA_BUFFER_START` when the player enters a buffering state, and `MEDIA_BUFFER_COMPLETE` when it exits:

```brightscript
adb = ADBMobile()

' Buffer starts
adb.mediaTrackEvent(adb.MEDIA_BUFFER_START)

' Buffer ends
adb.mediaTrackEvent(adb.MEDIA_BUFFER_COMPLETE)
```

>[!TAB Media Collection API]

Send a `bufferStart` POST to the [events endpoint](/help/implementation/media-collection-api/mc-api-ref/mc-api-events-req.md):

```json
{
  "playerTime": { "playhead": 45, "ts": 1699523820000 },
  "eventType": "bufferStart"
}
```

>[!ENDTABS]
