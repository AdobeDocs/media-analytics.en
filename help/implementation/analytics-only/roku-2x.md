---
title: Set up Roku 2.x for streaming media
description: Install and configure the Adobe Media SDK 2.x for Roku for Analytics-only streaming media implementations, including SceneGraph channels.
feature: Streaming Media
role: Developer
---
# Set up Roku 2.x for streaming media

The Adobe Media SDK 2.x for Roku (`adbmobile.brs`) sends streaming media data from Roku channels written in BrightScript directly to Adobe Analytics. It also collects audience data through Audience Manager and measures engagement through media events.

>[!NOTE]
>
>This page covers the Analytics-only Media SDK 2.x for Roku. For new implementations, Adobe recommends the [Roku Edge SDK](/help/implementation/edge/roku.md), which makes data available to Customer Journey Analytics, Adobe Journey Optimizer, and Real-Time CDP in addition to Adobe Analytics.

* **Prerequisites**:
  * Complete the [Analytics-only implementation overview](overview.md).
  * [Download the Media SDK for Roku](/help/getting-started/download-sdks.md).
  * Include an API in your media player to subscribe to player events, and an API that provides player information such as the media name and the playhead position.

## Install the SDK

The `AdobeMobileLibrary-2.*-Roku.zip` download contains two components:

* `adbmobile.brs`: the library file. Copy it into your channel's `pkg:/source/` directory.
* `ADBMobileConfig.json`: the SDK configuration file, customized for your app.

For SceneGraph channels, also copy `adbmobileTask.brs` and `adbmobileTask.xml` into your `pkg:/components/` directory. See [SceneGraph support](#scenegraph).

## Configure ADBMobileConfig.json

The configuration JSON has an exclusive `mediaHeartbeat` key for streaming media. Add `ADBMobileConfig.json` to your project source and set the `mediaHeartbeat`, `marketingCloud`, and `analytics` values:

```json
{
  "analytics": {
    "rsids": "your-report-suite-id",
    "server": "your-analytics-server"
  },
  "marketingCloud": {
    "org": "YOUR-MCORG-ID@AdobeOrg"
  },
  "mediaHeartbeat": {
    "server": "your-namespace.hb-api.omtrdc.net",
    "publisher": "your-publisher-id",
    "channel": "sample-channel",
    "ssl": true,
    "ovp": "sample-ovp",
    "sdkVersion": "sample-sdk",
    "playerName": "Roku Player"
  }
}
```

| Config parameter | Description |
| --- | --- |
| `server` | URL of the media tracking endpoint. See the [Analytics-only implementation overview](overview.md). |
| `publisher` | Content publisher unique identifier. |
| `channel` | Name of the content distribution channel. Reported as [Content channel](/help/implementation/variables/core/content-channel.md). |
| `ssl` | Whether SSL is used for tracking calls. |
| `ovp` | Name of the online video platform provider. |
| `sdkVersion` | Current version of your app or SDK. |
| `playerName` | Name of the player. Reported as [Content player name](/help/implementation/variables/core/content-player-name.md). |

>[!IMPORTANT]
>
>If `mediaHeartbeat` is incorrectly configured, the media module enters an error state and stops sending tracking calls. Ensure that your `marketingCloud.org` value includes `@AdobeOrg`.

## Initialize the SDK and process messages

Get an instance of the SDK with `ADBMobile()`. The Experience Cloud Visitor ID service generates a visitor ID that is included on all hits.

>[!IMPORTANT]
>
>Call `processMessages` and `processMediaMessages` in your main event loop every 250 ms so that the SDK sends pings properly.

```brightscript
adb = ADBMobile()

' In your main event loop, every ~250 ms:
adb.processMessages()
adb.processMediaMessages()
```

| Method | Description |
| --- | --- |
| `processMessages` | Passes queued Analytics events to the SDK. |
| `processMediaMessages` | Passes queued media events to the SDK, including automatic pings. |

## Track media events

Track each media event by calling its SDK method. See the **Roku 2.x** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact calls, builders, and constants.

A typical session begins by building a media object and calling `mediaTrackSessionStart`:

```brightscript
adb = ADBMobile()
mediaInfo = adb_media_init_mediainfo("Mr. Robot", "video-123", 128.0, adb.MEDIA_STREAM_TYPE_VOD, adb.MEDIA_TYPE_VIDEO)

contextData = { "a.media.show": "Mr. Robot" }

adb.mediaTrackSessionStart(mediaInfo, contextData)
```

The global `adb_media_init_*` builders create the media, ad, ad-break, chapter, and QoS objects used by the tracking calls:

| Builder | Signature |
| --- | --- |
| Media | `adb_media_init_mediainfo(name, id, length, streamType, mediaType)` |
| Ad | `adb_media_init_adinfo(name, id, position, length)` |
| Ad break | `adb_media_init_adbreakinfo(name, startTime, position)` |
| Chapter | `adb_media_init_chapterinfo(name, position, length, startTime)` |
| QoS | `adb_media_init_qosinfo(bitrate, startupTime, fps, droppedFrames)` |

Standard metadata is passed as an associative array of `a.media.*` keys (the SDK also defines named constants such as `MEDIA_VideoMetadataKeySHOW` for these keys). See the [Variables](/help/implementation/variables/overview.md) pages for the key that corresponds to each dimension.

## Configure the Experience Cloud Visitor ID, privacy, and logging

The following methods on the `ADBMobile()` instance manage identity, privacy, and debugging:

| Method | Description |
| --- | --- |
| `visitorMarketingCloudID()` | Retrieves the Experience Cloud ID (ECID). |
| `visitorSyncIdentifiers(identifiers)` | Sets additional customer IDs for the same visitor. |
| `setAdvertisingIdentifier(rida)` | Sets the Roku ID for Advertising (RIDA). Get it with the Roku [`getRIDA()`](https://developer.roku.com/docs/references/brightscript/interfaces/ifdeviceinfo.md#getrida-as-dynamic) API. |
| `getAllIdentifiers()` | Returns all identifiers stored by the SDK, including Analytics, Visitor, Audience Manager, and custom identifiers. |
| `setPrivacyStatus(status)` | Sets the privacy status. Pass `adb.PRIVACY_STATUS_OPT_IN` or `adb.PRIVACY_STATUS_OPT_OUT`. See [Privacy](/help/implementation/opt-out-privacy.md). |
| `getPrivacyStatus()` | Returns the current privacy status. |
| `setDebugLogging(flag)` | Enables or disables debug logging. |
| `getDebugLogging()` | Returns `true` if debug logging is enabled. |

## SceneGraph support {#scenegraph}

The Roku SceneGraph XML framework cannot call the legacy BrightScript SDK APIs directly, because the SDK uses components (such as threads) that are not available to a SceneGraph app. To bridge this gap, the SDK provides a connector that returns a SceneGraph-compatible instance exposing the same APIs, plus a callback mechanism for APIs that return data.

The bridge has three parts:

* **`adbmobileTask` node**: a SceneGraph task node that executes SDK APIs on a background thread and returns data to your scenes.
* **Connector instance**: wraps all legacy public APIs and communicates with the `adbmobileTask` node.
* **`API_RESPONSE` callback**: the field your app observes to receive return values from getter APIs.

To initialize the SDK in a SceneGraph channel:

1. Import `adbmobile.brs` into your scene:

   ```brightscript
   <script type="text/brightscript" uri="pkg:/source/adbmobile.brs" />
   ```

1. Create the `adbmobileTask` node, get the connector instance, and load the SceneGraph constants:

   ```brightscript
   m.adbmobileTask = createObject("roSGNode", "adbmobileTask")
   m.adbmobile = ADBMobile().getADBMobileConnectorInstance(m.adbmobileTask)
   m.adbmobileConstants = m.adbmobile.sceneGraphConstants()
   ```

1. Register a callback to receive response objects for APIs that return data:

   ```brightscript
   m.adbmobileTask.ObserveField(m.adbmobileConstants.API_RESPONSE, "onAdbmobileApiResponse")

   function onAdbmobileApiResponse() as void
       responseObject = m.adbmobileTask[m.adbmobileConstants.API_RESPONSE]
       if responseObject <> invalid
           methodName = responseObject.apiName
           retVal = responseObject.returnValue
           if methodName = m.adbmobileConstants.PRIVACY_STATUS
               print "Privacy status: " + retVal
           end if
       end if
   end function
   ```

The connector instance (`m.adbmobile`) exposes the same media methods as the legacy SDK (`mediaTrackSessionStart`, `mediaTrackPlay`, `mediaTrackPause`, `mediaTrackComplete`, `mediaTrackSessionEnd`, `mediaTrackError`, `mediaTrackEvent`, `mediaUpdatePlayhead`, and `mediaUpdateQoS`) so the calls shown on the event and variable pages work the same way. Setter APIs are called directly; getter APIs return their values through the `API_RESPONSE` callback.

## Next step

Once your implementation is complete, you can [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

>[!MORELIKETHIS]
>
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
>* [Roku Edge SDK](/help/implementation/edge/roku.md)
