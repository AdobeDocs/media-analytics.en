---
title: How to set up a web implementation for Analytics for Streaming Media
description: Learn how to implement Adobe Streaming Media for web apps.
feature: Media Analytics
role: User, Admin, Data Engineer
exl-id: aed561d0-defc-4be5-87d3-0f331cdfab34
---
# Install Media Analytics using JavaScript {#install-web-sdks}

The information on this page describes how to install the web standalone SDK and set up JavaScript.

Alternatively, you can use the Adobe Media Analytics extension to implement Analytics, as described in [Implement Analytics using the Media Analytics extension](/help/implementation/media-sdk/setup/web-implementation-tags.md).

## Prerequisites {#prerequesites}

* **Obtain valid configuration parameters**

   These parameters can be obtained from an Adobe representative after you set up your analytics account.

* **Implement `AppMeasurement` and `Experience Cloud Identity Service` for JavaScript in your media application**

   For more information, see [Implementing Analytics Using JavaScript](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html) and [Implementing Experience Cloud Identity  Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-analytics.html).

* **Include the following APIs in your media player**

    * *An API to subscribe to player events* - The Media SDK requires that you call a set of simple APIs when events occur in your player.
    * *An API that provides player information* - This includes information about currently playing media, ads, and chapter.

## Set up JavaScript 3.x {#set-up-javascript}

1. Add your [downloaded](/help/getting-started/download-sdks.md) library to your project. Create local references to the classes for convenience.

   1. Expand the `MediaSDK-js-v3*.zip` file that you downloaded.
   1. Verify that the `MediaSDK.js` file exists in the `libs` directory.

   1. Host the `MediaSDK.js` file.

      This core JavaScript file must be hosted on a web server that is accessible to all pages on your site. You need the path to these files for the next step.

   1. Reference `MediaSDK.js` on all site pages.

      Include `MediaSDK` for JavaScript by adding the following line of code in the `<head>` or `<body>` tag on each page. For example:

      ```html
      <script type="text/javascript" src="https://INSERT-DOMAIN-AND-PATH-TO-CODE-HERE/MediaSDK.js"></script>
      ```

   1. To quickly verify that the library was successfully imported, check `ADB.Media` is exported on Window object.

      >[!NOTE]
      >
      >The JavaScript SDK is compliant with the AMD and CommonJS module specifications, and `MediaSDK.js` can also be used with compatible module loaders.

1. Create an instance of `AppMeasurement` and configure `visitor`.

   The Media SDK configuration requires an instance of `AppMeasurement` with `visitor` configured.

   ``` js
    var appMeasurement = new AppMeasurement("<rsid>");
    appMeasurement.visitor = visitor;
    appMeasurement.trackingServer = "<visitor_namespace>.sc.omtrdc.net";
   ```

1. Configure Media SDK

   Media SDK should be configured once per webpage and the configuration applies to all the tracker instances created.

   >[!IMPORTANT]
   >
   > Media SDK (3.x) uses Media Collection API for tracking media which is different from the HB endpoint used in 2.x SDKs. Contact your Adobe representative to get more information.

   Here is a sample `MediaConfig` initialization:

   ```js

    // Create MediaConfig object (same as above)
    var mediaConfig = new ADB.MediaConfig();
    mediaConfig.trackingServer = Configuration.MEDIA_COLLECTION_ENDPOINT;
    mediaConfig.playerName = Configuration.PLAYER_NAME;
    mediaConfig.channel = Configuration.CHANNEL;
    mediaConfig.appVersion = Configuration.APP_VERSION;
    mediaConfig.debugLogging = false;
    mediaConfig.ssl = true;

    ADB.Media.configure(mediaConfig, appMeasurement);

   ```

1. Create the `MediaTracker` instance.

   After configuring Media SDK, tracker instances for tracking media content can be created using `getInstance` API.

   ```js

   var tracker = ADB.Media.getInstance();

   ```

   >[!IMPORTANT]
   >
   >Make sure that your `tracker` instance is accessible and does not get deallocated until the end of the media session. This instance will be used for tracking all the following events for that session.

## Migrate from JavaScript 2.x to 3.x

For detailed information about migrating from 2.x to 3.x, see [2.x to 3.x Migration.](https://adobe-marketing-cloud.github.io/media-sdks/reference/javascript_3x/MigrationGuide.html)

For legacy content, see [Legacy implementations](/help/legacy/media-sdk/setup/setup-overview.md)
