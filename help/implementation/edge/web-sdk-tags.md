---
title: Set up the Web SDK tag extension for streaming media
description: Configure streaming media collection in the Adobe Experience Platform Web SDK tag extension.
feature: Streaming Media
role: Developer
---
# Set up the Web SDK tag extension for streaming media

The Adobe Experience Platform Web SDK tag extension lets you configure streaming media collection in the Data Collection UI, with no `alloy.js` configuration code. This page covers the Tags configuration. To configure the Web SDK in code instead, see [Set up the Web SDK for streaming media](web-sdk.md).

* **Prerequisites**:
  * Complete the [Edge implementation overview](overview.md) (schema, dataset, datastream with [!UICONTROL Media Analytics] enabled).
  * Install and configure the Web SDK tag extension. See the [Web SDK tag extension overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/overview).

## Configure streaming media in the extension

1. In the Data Collection UI, open your web property and select **[!UICONTROL Extensions]**.
1. On the installed **Adobe Experience Platform Web SDK** extension, select **[!UICONTROL Configure]**.
1. Expand the **[!UICONTROL Streaming Media]** section and set the following:
   * **[!UICONTROL Channel]**: The channel name reported with each session.
   * **[!UICONTROL Player name]**: The name of the media player in use.
   * **[!UICONTROL Application version]**: The version of your player application.
   * **[!UICONTROL Main ping interval]** and **[!UICONTROL Ad ping interval]**: The ping cadence (in seconds) for main content and ads.
1. Save the extension configuration and publish your changes.

## Track media events

With the extension configured, send each media event with the **[!UICONTROL Send Event]** action (or the `sendEvent` command). See the **Web SDK** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact payloads.

## Next step

Once your implementation is complete, you can [Set up reporting for Edge implementations](/help/reporting/setup/edge-reporting.md).

>[!MORELIKETHIS]
>
>* [Web SDK tag extension overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/overview)
>* [Set up the Web SDK for streaming media (in code)](web-sdk.md)
>* [Events overview](/help/implementation/events/overview.md)
