---
title: Set up Roku for streaming media
description: Configure the Adobe Experience Platform Roku SDK to send streaming media data to the Edge Network.
feature: Streaming Media
role: Developer
---
# Set up Roku for streaming media

The [Adobe Experience Platform Roku SDK](https://github.com/adobe/aepsdk-roku) (BrightScript) collects media session data in your Roku channel and sends it to the Edge Network. Roku is configured in code; it does not use Tags.

* **Prerequisites**:
  * Complete the [Edge implementation overview](overview.md) (schema, dataset, datastream with [!UICONTROL Media Analytics] enabled).
  * Download the SDK from [GitHub releases](https://github.com/adobe/aepsdk-roku/releases) and add it to your channel, as described in the [getting started guide](https://github.com/adobe/aepsdk-roku/blob/main/Documentation/getting-started.md).

## Configure the AEP Roku SDK for media

Initialize the SDK and set the datastream and media configuration:

```brightscript
m.aepSdk = AdobeAEPSDKInit()
ADB_CONSTANTS = AdobeAEPSDKConstants()

configuration = {}
configuration[ADB_CONSTANTS.CONFIGURATION.EDGE_CONFIG_ID] = "<datastreamID>"
configuration[ADB_CONSTANTS.CONFIGURATION.MEDIA_CHANNEL] = "sample_channel"
configuration[ADB_CONSTANTS.CONFIGURATION.MEDIA_PLAYER_NAME] = "player_name"
m.aepSdk.updateConfiguration(configuration)
```

Then open a session with `createMediaSession`:

```brightscript
m.aepSdk.createMediaSession({
    "xdm": {
        "eventType": "media.sessionStart",
        "mediaCollection": {
            "sessionDetails": { "name": "video-123", "length": 128, "contentType": "vod", "streamType": "video" },
            "playhead": 0
        }
    }
})
```

>[!IMPORTANT]
>
>Send a `media.ping` event at least once per second with the latest playhead value during playback. The AEP Roku SDK relies on these pings to function correctly.

For configuration keys and the full API, see the [AEP Roku SDK API reference](https://github.com/adobe/aepsdk-roku/blob/main/Documentation/api-reference.md).

## Track media events

After the session is open, send each media event with `sendMediaEvent`. See the **Roku** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact payloads.

## Next step

Once your implementation is complete, you can [Set up reporting for Edge implementations](/help/reporting/setup/edge-reporting.md).

>[!MORELIKETHIS]
>
>* [Adobe Experience Platform Roku SDK](https://github.com/adobe/aepsdk-roku)
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
