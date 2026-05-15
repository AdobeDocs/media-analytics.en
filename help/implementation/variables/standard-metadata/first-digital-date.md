---
title: First digital date
description: Set the date the content first aired on a digital platform. Adobe recommends YYYY-MM-DD format.
feature: Streaming Media
role: Developer
---

# First digital date

>[!BEGINSHADEBOX]

*This page covers data collection for the **First digital date** variable. See [First digital date](/help/reporting/dimensions/first-digital-date.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The first digital date variable is the date the content first aired on any digital platform. Any date format is accepted but Adobe recommends `YYYY-MM-DD` for consistency. Use alongside [First air date](/help/implementation/variables/standard-metadata/first-air-date.md) to compare digital release timing with original broadcast.

| Property | Value |
| --- | --- |
| **Context data variable** | `a.media.digitalDate` |
| **XDM collection field** | [`mediaCollection.sessionDetails.firstDigitalDate`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Audience Manager trait** | `c_contextdata.a.media.digitalDate` |
| **Required** | No |
| **Sent with** | [Session start](/help/implementation/events/session/session-start.md), session close |

## Web SDK

Set `firstDigitalDate` inside `mediaCollection.sessionDetails` when calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview):

```javascript
alloy("sendEvent", {
  xdm: {
    eventType: "media.sessionStart",
    mediaCollection: {
      sessionDetails: {
        firstDigitalDate: "2016-01-25"
      },
      playhead: 0
    }
  }
});
```

## Mobile SDK

Pass the first digital date as a metadata key in the HashMap argument to `trackSessionStart`. Use `MediaConstants.VideoMetadataKeys.FIRST_DIGITAL_DATE`.

**iOS (Swift)**

```swift
var metadata: [String: String] = [:]
metadata[MediaConstants.VideoMetadataKeys.FIRST_DIGITAL_DATE] = "2016-01-25"

tracker.trackSessionStart(info: mediaObject, metadata: metadata)
```

**Android (Kotlin)**

```kotlin
val metadata = HashMap<String, String>()
metadata[MediaConstants.VideoMetadataKeys.FIRST_DIGITAL_DATE] = "2016-01-25"

tracker.trackSessionStart(mediaInfo, metadata)
```

## Roku (BrightScript)

Use `createMediaSession` to set `firstDigitalDate` inside `sessionDetails`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": {
                "firstDigitalDate": "2016-01-25"
            },
            "playhead": 0
        }
    }
})
```

## Media Edge API

Call the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) endpoint with `firstDigitalDate` inside `mediaCollection.sessionDetails`:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.sessionStart",
      "mediaCollection": {
        "sessionDetails": {
          "name": "video-123",
          "length": 128,
          "contentType": "vod",
          "playerName": "HTML5 Player",
          "channel": "Sports",
          "firstDigitalDate": "2016-01-25"
        },
        "playhead": 0
      }
    }
  }]
}
```

## Media SDK

Pass the first digital date in the `contextData` object using `ADB.Media.VideoMetadataKeys.FirstDigitalDate`:

```javascript
var contextData = {};
contextData[ADB.Media.VideoMetadataKeys.FirstDigitalDate] = "2016-01-25";

tracker.trackSessionStart(mediaInfo, contextData);
```

## Media Collection API

Include `media.firstDigitalDate` in the `params` object:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.firstDigitalDate": "2016-01-25"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.
