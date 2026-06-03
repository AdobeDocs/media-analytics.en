---
title: App version
description: Configure the version string of your media player application.
feature: Streaming Media
role: Developer
---

# App version

>[!BEGINSHADEBOX]

*This page covers data collection for the **App version** variable. See [App version](/help/reporting/dimensions/app-version.md) for the corresponding reporting dimension.*

>[!ENDSHADEBOX]

The app version variable identifies the version of your media player application. Set it once during SDK initialization; the value is automatically included in every subsequent session start request. Use a version string that matches your application's release cycle (for example, `"2.1.0"` or `"prod-YYYY-03-15"`).

>[!NOTE]
>
>This field captures the version of your **media player application**, not Adobe's SDK library. Adobe's own SDK library version is collected automatically as a separate internal field.

| Property | Value |
| --- | --- |
| **XDM collection field** | [`xdm.mediaCollection.sessionDetails.appVersion`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-collection) |
| **Media Collection API param** | `media.sdkVersion` |
| **Required** | No |
| **Sent with** | [Session start](/help/implementation/events/session/session-start.md) |

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

Set `appVersion` in the `streamingMedia` configuration object when calling [`configure`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/configure/streamingmedia):

```javascript
alloy("configure", {
  streamingMedia: {
    channel: "Sports Channel",
    playerName: "HTML5 Player",
    appVersion: "2.1.0",
    mainPingInterval: 10,
    adPingInterval: 10
  }
});
```

>[!TAB iOS]

Set `edgeMedia.appVersion` in the app configuration before initializing the media tracker:

```swift
var config: [String: Any] = [:]
config["edgeMedia.channel"] = "sample_channel"
config["edgeMedia.playerName"] = "player_name"
config["edgeMedia.appVersion"] = "2.1.0"
MobileCore.updateConfiguration(config)
```

>[!TAB Android]

Set `edgeMedia.appVersion` in the app configuration before initializing the media tracker:

```kotlin
val config: Map<String, Any> = mapOf(
    "edgeMedia.channel" to "sample_channel",
    "edgeMedia.playerName" to "player_name",
    "edgeMedia.appVersion" to "2.1.0"
)
MobileCore.updateConfiguration(config)
```

>[!TAB Roku]

Set the app version in the SDK configuration using `ADB_CONSTANTS.CONFIGURATION.MEDIA_APP_VERSION`:

```brightscript
ADB_CONSTANTS = AdobeAEPSDKConstants()
configuration = {}
configuration[ADB_CONSTANTS.CONFIGURATION.EDGE_CONFIG_ID] = "<YOUR_CONFIG_ID>"
configuration[ADB_CONSTANTS.CONFIGURATION.MEDIA_CHANNEL] = "channel_name"
configuration[ADB_CONSTANTS.CONFIGURATION.MEDIA_PLAYER_NAME] = "player_name"
configuration[ADB_CONSTANTS.CONFIGURATION.MEDIA_APP_VERSION] = "2.1.0"
m.aepSdk.updateConfiguration(configuration)
```

>[!TAB Media Edge API]

Include `appVersion` in the `sessionDetails` object of the [sessionStart](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/sessions/#sessionstart) request:

```json
{
  "events": [{
    "xdm": {
      "eventType": "media.sessionStart",
      "mediaCollection": {
        "sessionDetails": {
          "name": "video-123",
          "length": 300,
          "contentType": "vod",
          "playerName": "HTML5 Player",
          "channel": "Sports",
          "appVersion": "2.1.0"
        },
        "playhead": 0
      }
    }
  }]
}
```

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

Set `appVersion` on the `MediaConfig` object before calling `ADB.Media.configure`:

```javascript
var mediaConfig = new ADB.MediaConfig();
mediaConfig.playerName = "player_name";
mediaConfig.channel = "sample_channel";
mediaConfig.appVersion = "2.1.0";
ADB.Media.configure(mediaConfig, appMeasurement);
```

>[!TAB Chromecast]

Set `sdkVersion` in the `mediaHeartbeat` section of the ADBMobile configuration. This field captures your player application version, not the Chromecast SDK library version.

```javascript
var ADBMobileConfig = {
  "mediaHeartbeat": {
    "server": "obumobile5.hb-api.omtrdc.net",
    "publisher": "<YOUR_PUBLISHER_ID>@AdobeOrg",
    "channel": "sample-channel",
    "ssl": true,
    "playerName": "Chromecast Player",
    "sdkVersion": "2.1.0"
  }
};
```

>[!TAB Media Collection API]

Include `media.sdkVersion` in the `params` object of your `sessionStart` POST request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "media.playerName": "sample-html5-api-player",
    "media.sdkVersion": "2.1.0",
    "media.channel": "sample-channel"
  }
}
```

See the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md) for the full request structure.

>[!ENDTABS]
