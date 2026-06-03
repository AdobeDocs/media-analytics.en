---
title: Set up JavaScript for streaming media
description: Install and configure the Media SDK for JavaScript (3.x) for Analytics-only streaming media implementations.
feature: Streaming Media
role: Developer
---
# Set up JavaScript for streaming media

The Media SDK for JavaScript (3.x) sends streaming media data directly to Adobe Analytics. This page covers the manual JavaScript installation. To deploy the SDK through Tags instead, see [Set up the Media Analytics tag extension](javascript-tags.md). For new implementations, consider using the [Web SDK](/help/implementation/edge/web-sdk.md) to send data to Adobe Analytics through an Edge Network datastream.

* **Prerequisites**:
  * Complete the [Analytics-only implementation overview](overview.md).
  * Implement [AppMeasurement](https://experienceleague.adobe.com/en/docs/analytics/implementation/js/overview) and the [Visitor ID Service](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/appmeasurement).
  * [Download the Media SDK for JavaScript](/help/getting-started/download-sdks.md).

## Install and configure the SDK

1. Host `MediaSDK.js` (from the downloaded `libs` directory) on a web server accessible to all pages, and reference it on each page:

   ```html
   <script type="text/javascript" src="https://INSERT-DOMAIN-AND-PATH/MediaSDK.js"></script>
   ```

1. Configure the Media SDK once per page, passing the `appMeasurement` instance that you set up as a prerequisite:

   ```js
   var mediaConfig = new ADB.MediaConfig();
   mediaConfig.trackingServer = "<media_collection_server>";
   mediaConfig.playerName = "player_name";
   mediaConfig.channel = "sample_channel";
   mediaConfig.appVersion = "app_version";
   mediaConfig.ssl = true;

   ADB.Media.configure(mediaConfig, appMeasurement);
   ```

   >[!NOTE]
   >
   >The `mediaConfig.trackingServer` variable is your **media collection server** (for example, `[namespace].hb-api.omtrdc.net`). This collection server is distinct from the Analytics tracking server configured within the AppMeasurement instance.

1. Create a tracker instance with `getInstance`. Keep the instance accessible for the entire media session:

   ```js
   var tracker = ADB.Media.getInstance();
   ```

## Track media events

With the tracker created, track each media event using its tracker method. See the **Media SDK JS 3.x** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact calls.

## Next step

Once your implementation is complete, you can [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

>[!MORELIKETHIS]
>
>* [Media SDK for JavaScript 3.x API reference](https://github.com/Adobe-Marketing-Cloud/media-sdks/blob/master/sdks/js/3.x/docs/APIReference.md)
>* [Migrate from JS SDK 2.x to 3.x](https://github.com/Adobe-Marketing-Cloud/media-sdks/blob/master/sdks/js/3.x/docs/MigrationGuide.md)
>* [Set up the Media Analytics tag extension](javascript-tags.md)
>* [Events overview](/help/implementation/events/overview.md)
