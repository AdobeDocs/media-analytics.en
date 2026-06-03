---
title: Set up Android for streaming media
description: Configure the Adobe Experience Platform Mobile SDK on Android to send streaming media data to the Edge Network.
feature: Streaming Media
role: Developer
---
# Set up Android for streaming media

The Adobe Streaming Media for Edge Network extension (`EdgeMedia`) collects media session data in your Android app and sends it to the Edge Network. This page covers in-code configuration. To configure the SDK through a Tags mobile property instead, see [Set up Android for streaming media with Tags](android-tags.md).

* **Prerequisites**:
  * Complete the [Edge implementation overview](overview.md) (schema, dataset, datastream with [!UICONTROL Media Analytics] enabled).
  * Add the `Core`, `Edge`, `EdgeIdentity`, and `EdgeMedia` extensions to your app. See [Adobe Streaming Media for Edge Network](https://developer.adobe.com/client-sdks/edge/media-for-edge-network/) for installation and registration.

## Configure media for Android

Set the media configuration keys when you initialize the SDK:

```kotlin
val configuration = mapOf(
  "edgeMedia.channel" to "sample_channel",
  "edgeMedia.playerName" to "player_name",
  "edgeMedia.appVersion" to "app_version"
)
MobileCore.updateConfiguration(configuration)
```

Then create a tracker to manage a media session:

```kotlin
val tracker = Media.createTracker()
```

For configuration keys and the full tracker API, see the [Media for Edge Network API reference](https://developer.adobe.com/client-sdks/edge/media-for-edge-network/api-reference/).

## Track media events

With the tracker created, track each media event using its tracker method. See the **Android** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact calls.

## Next step

Once your implementation is complete, you can [Set up reporting for Edge implementations](/help/reporting/setup/edge-reporting.md).

>[!MORELIKETHIS]
>
>* [Adobe Streaming Media for Edge Network](https://developer.adobe.com/client-sdks/edge/media-for-edge-network/)
>* [Set up Android for streaming media with Tags](android-tags.md)
>* [Events overview](/help/implementation/events/overview.md)
