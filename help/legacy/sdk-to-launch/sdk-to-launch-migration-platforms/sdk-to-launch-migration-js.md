---
title: Migrating from the Standalone Media SDK to Adobe Launch - Web (JS)
description: Learn how to migrate from the Media SDK to Launch for JS.
exl-id: 19b506b2-3070-4a5e-9732-a5cd0867afde
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/N4Fcbg3R9tT9cjUcaw-kcUm6h-QT8TYwatdCe1IdsaM
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
  - id: c069c44e-5426-4c1a-accc-8028662f2fde
    internal-label: Functions
  - id: df312454-73c4-43f6-a90e-18f5043f074c
    internal-label: Tags
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Migrating from the standalone Media SDK to Adobe Launch - Web (JS)

>[!NOTE]
>Adobe Experience Platform Launch has been rebranded as a suite of data collection technologies in Experience Platform. Several terminology changes have rolled out across the product documentation as a result. Please refer to the following [document](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html?lang=en) for a consolidated reference of the terminology changes.

## Feature differences

* *Launch* - Launch provides you with a UI that walks you through setting up, configuring, and deploying your web-based media tracking solutions. Launch improves upon Dynamic Tag Management (DTM).
* *Media SDK* - The Media SDK provides you with media tracking libraries designed for specific platforms (e.g.: Android, iOS, etc.). Adobe recommends Media SDK for tracking media usage in your Mobile Apps.

## Configuration

### Standalone Media SDK

In the standalone Media SDK, you configure the tracking configuration in the app
and pass it to the SDK when you create the tracker.

```javascript
//Media Heartbeat initialization
var mediaConfig = new MediaHeartbeatConfig();
mediaConfig.trackingServer = "namespace.hb.omtrdc.net";
mediaConfig.playerName = "html5-player";
mediaConfig.channel = "sample-channel";
mediaConfig.ovp = "video-provider";
mediaConfig.appVersion = "v2.0.0"
mediaConfig.ssl = true;
mediaConfig.debugLogging = true;
```

In addition to the `MediaHeartbeat` configuration, the page must configure and pass
the `AppMeasurement` instance and `VisitorAPI` instance for media tracking in order
to work properly.

### Launch Extension

1. In Experience Platform Launch, click the [!UICONTROL Extensions] tab for your
    web property.
1. On the [!UICONTROL Catalog] tab, locate the Adobe Media Analytics for Audio and
    Video extension, and click [!UICONTROL Install].
1. In the extension settings page, configure the tracking parameters.
    The Media extension will use the configured parameters for tracking.

    ![](assets/launch_config_js.png)

[Launch User Guide - Install & configure the media extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics/overview.html#install-and-configure-the-ma-extension)

## Tracker creation differences

### Media SDK

1. Add the Media Analytics library to your development project.
1. Create a config object (`MediaHeartbeatConfig`).
1. Implement the delegate protocol, exposing the `getQoSObject()` and `getCurrentPlaybackTime()` functions.
1. Create a Media Heartbeat instance (`MediaHeartbeat`).

```
// Media Heartbeat initialization
var mediaConfig = new MediaHeartbeatConfig();
...
// Configuration settings
mediaConfig.trackingServer = Configuration.HEARTBEAT.TRACKING_SERVER;
...
// Implement Media Delegate (Quality of Service and Playhead)
var mediaDelegate = new MediaHeartbeatDelegate();
...
mediaDelegate.getQoSObject = function() {
    return MediaHeartbeat.createQoSObject(<bitrate>, <startuptime>, <fps>, <droppedFrames>);
    ...
}
...
// Create your tracker
this.mediaHeartbeat = new MediaHeartbeat(mediaDelegate, mediaConfig, appMeasurement);
```

### Launch

Launch offers two approaches to creating the tracking infrastructure. Both approaches use the Media Analytics Launch Extension:

1. Use the media tracking APIs from a web page.

    In this scenario, the Media Analytics Extension exports the media tracking APIs to a configured variable in the global window object:

    ```
    window["CONFIGURED_VARIABLE_NAME"].MediaHeartbeat.getInstance
    ```

1. Use the media tracking APIs from another Launch extension.

    In this scenario, you use the media tracking APIs exposed by the `get-instance` and `media-heartbeat` Shared Modules.

    >[!NOTE]
    >
    >Shared Modules are not available for use in web pages. You can only use Shared Modules from another extension.

    Create a `MediaHeartbeat` instance using the `get-instance` Shared Module.
    Pass a delegate object to `get-instance` that exposes `getQoSObject()` and `getCurrentPlaybackTime()` functions.

    ```
    var getMediaHeartbeatInstance =
    turbine.getSharedModule('adobe-video-analytics', 'get-instance');
    ```

    Access `MediaHeartbeat` constants via the `media-heartbeat` Shared Module.

## Related Documentation

### Media SDK

* [Set up JavaScript 2.x](/help/legacy/media-sdk/setup/setup-javascript/set-up-js-2.md)
* [Media SDK JS API](https://adobe-marketing-cloud.github.io/media-sdks/reference/javascript/MediaHeartbeat.html)

### Launch

* [Launch overview](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
* [Media Analytics Extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics/overview.html)
