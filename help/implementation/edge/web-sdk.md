---
title: Set up the Web SDK for streaming media
description: Configure the Adobe Experience Platform Web SDK (alloy.js) to send streaming media data to the Edge Network.
feature: Streaming Media
role: Developer
---
# Set up the Web SDK for streaming media

The `streamingMedia` component of the Adobe Experience Platform [Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/js-overview) (`alloy.js`, version 2.20.0 or later) collects media session data on your website and sends it to the Edge Network. This page covers the in-code (`alloy.js`) configuration. To configure the Web SDK through Tags instead, see [Set up the Web SDK tag extension for streaming media](web-sdk-tags.md).

* **Prerequisites**:
  * Complete the [Edge implementation overview](overview.md) (schema, dataset, datastream with [!UICONTROL Media Analytics] enabled).
  * Install Web SDK 2.20.0 or later. See [Install the Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/install/overview).

## Configure the streamingMedia component

Add the `streamingMedia` component to your `alloy` configuration:

```js
alloy("configure", {
  edgeConfigId: "<datastreamID>",
  streamingMedia: {
    channel: "sample_channel",
    playerName: "player_name",
    appVersion: "app_version",
    mainPingInterval: 10,
    adPingInterval: 10
  }
});
```

For complete configuration details, see the [`streamingMedia` command](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/configure/streamingmedia).

### Migrating from the Media JS SDK

If you are moving from the Media JS (3.x) SDK, the Web SDK [`getMediaAnalyticsTracker`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/getmediaanalyticstracker) command returns a tracker instance that exposes the same APIs as the [3.x Media SDK](/help/implementation/analytics-only/javascript.md), so your existing tracking calls continue to work.

## Track media events

With the SDK configured, send each media event by calling [`sendEvent`](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/commands/sendevent/overview). See the **Web SDK** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact payloads.

## Next step

Once your implementation is complete, you can [Set up reporting for Edge implementations](/help/reporting/setup/edge-reporting.md).

>[!MORELIKETHIS]
>
>* [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/collection/js/js-overview)
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
