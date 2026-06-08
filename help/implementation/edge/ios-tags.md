---
title: Set up iOS for streaming media with Tags
description: Configure streaming media collection for iOS using the Adobe Streaming Media for Edge Network tag extension.
feature: Streaming Media
role: Developer
---
# Set up iOS for streaming media with Tags

You can configure streaming media collection for your iOS or tvOS app through a Tags mobile property, with the media settings managed in the Data Collection UI. This page covers the Tags configuration. To configure the SDK in code instead, see [Set up iOS for streaming media](ios.md).

* **Prerequisites**:
  * Complete the [Edge implementation overview](overview.md) (schema, dataset, datastream with [!UICONTROL Media Analytics] enabled).
  * Create a mobile property in the Data Collection UI. See [Adobe Streaming Media for Edge Network](https://developer.adobe.com/client-sdks/edge/media-for-edge-network/).

## Configure the extension

1. In the Data Collection UI, open your mobile property and select **[!UICONTROL Extensions]**.
1. On the **[!UICONTROL Catalog]** tab, locate the **Adobe Streaming Media for Edge Network** extension and select **[!UICONTROL Install]**.
1. Set the following, then save:
   * **[!UICONTROL Channel]**: the channel name reported with each session.
   * **[!UICONTROL Player name]**: the name of the media player in use.
   * **[!UICONTROL Application version]**: the version of your player application.
1. Publish your changes, then add the `AEPCore`, `AEPEdge`, `AEPEdgeIdentity`, and `AEPEdgeMedia` dependencies to your app and register them with Mobile Core.

## Track media events

With the property published and the tracker created, track each media event using its tracker method. See the **iOS** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact calls.

## Next step

Once your implementation is complete, you can [Set up reporting for Edge implementations](/help/reporting/setup/edge-reporting.md).

>[!MORELIKETHIS]
>
>* [Adobe Streaming Media for Edge Network](https://developer.adobe.com/client-sdks/edge/media-for-edge-network/)
>* [Set up iOS for streaming media (in code)](ios.md)
>* [Events overview](/help/implementation/events/overview.md)
