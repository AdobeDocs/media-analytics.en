---
title: Get Media SDKs, extensions, and APIs
description: Links to SDK downloads for available platforms, including Android, iOS, JavaScript, Chromecast, and Roku.
uuid: a619fbb8-693e-4583-8dad-0ff875e715f8
exl-id: d211fa2e-d5b0-4e9f-bdb7-eda838194f3d
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/-L2tSDNue-GheYE-krKkpnOh05s5GKZZBz5sFXsBJ3I
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
  - id: c77ba355-6681-41fe-b719-563d3f507fdb
    internal-label: Mobile SDK
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
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Get Media SDKs, extensions, and APIs

## Edge implementations (recommended) {#edge-sdks}

Edge implementations collect data once and deliver it through Adobe Experience Platform Edge Network to multiple destinations: Adobe Analytics, Customer Journey Analytics, Adobe Journey Optimizer, and Real-Time CDP. For platforms without a native SDK (such as Smart TVs, gaming consoles, and set-top boxes), use the Media Edge API.

| | Documentation | Sample |
|:---:|---|---|
| [![JavaScript icon](assets/javascript-icon.png)](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)<br>[Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview) | [Set up the Web SDK for streaming media](/help/implementation/edge/web-sdk.md) | [Sample](https://github.com/adobe/alloy-samples/blob/main/media-collection/STANDALONE.md) |
| [![Extension icon](assets/plug.svg)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/web-sdk/overview.html)<br>[Web SDK tag extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/web-sdk/overview.html) | [Set up the Web SDK tag extension for streaming media](/help/implementation/edge/web-sdk-tags.md) | [Sample](https://github.com/adobe/alloy-samples/blob/main/media-collection/TAGS_IMPL.md) |
| [![Android icon](assets/android.png)](https://github.com/adobe/aepsdk-media-android)<br>[Android SDK](https://github.com/adobe/aepsdk-media-android) | [Set up Android for streaming media](/help/implementation/edge/android.md) | [Sample](https://github.com/adobe/aepsdk-media-android/tree/main/code/testapp) |
| [![Apple iOS icon](assets/apple.png)](https://github.com/adobe/aepsdk-media-ios)<br>[iOS / tvOS SDK](https://github.com/adobe/aepsdk-media-ios) | [Set up iOS for streaming media](/help/implementation/edge/ios.md) | [Sample](https://github.com/adobe/aepsdk-media-ios/tree/main/TestApp) |
| [![Extension icon](assets/plug.svg)](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/)<br>[Android tag extension](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/) | [Set up the Android tag extension for streaming media](/help/implementation/edge/android-tags.md) | |
| [![Extension icon](assets/plug.svg)](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/)<br>[iOS / tvOS tag extension](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/) | [Set up the iOS tag extension for streaming media](/help/implementation/edge/ios-tags.md) | |
| [![Roku icon](assets/roku-icon.png)](https://github.com/adobe/aepsdk-roku)<br>[Roku Edge SDK](https://github.com/adobe/aepsdk-roku) | [Set up Roku Edge for streaming media](/help/implementation/edge/roku.md) | [Sample](https://github.com/adobe/aepsdk-roku/tree/main/sample/simple-videoplayer-channel) |
| [![API icon](assets/api.png)](https://developer.adobe.com/data-collection-apis/docs/api/media-edge)<br>[Media Edge API](https://developer.adobe.com/data-collection-apis/docs/api/media-edge) | [Set up Media Edge API](/help/implementation/edge/media-edge-api.md) | [Sample](https://developer.adobe.com/data-collection-apis/docs/getting-started/media-edge-examples) |

## Analytics-only implementations {#analytics-only-sdks}

These SDKs and extensions send data directly to Adobe Analytics. For new implementations, use the Edge implementations above. To bring existing Analytics data into Customer Journey Analytics or other Experience Platform applications, use the [Analytics source connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/analytics).

| | Documentation | Sample |
|:---:|---|---|
| [![JavaScript icon](assets/javascript-icon.png)](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases/tag/js-v3.0.2)<br>[Media SDK 3.x](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases/tag/js-v3.0.2) | [Set up JavaScript for streaming media](/help/implementation/analytics-only/javascript.md) | [Sample](https://github.com/Adobe-Marketing-Cloud/media-sdks/tree/master/sdks/js/3.x) |
| [![Extension icon](assets/plug.svg)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics-3x/overview.html?lang=en)<br>[Media Extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics-3x/overview.html?lang=en) | [Set up JavaScript using tags for streaming media](/help/implementation/analytics-only/javascript-tags.md) | [Sample](https://github.com/Adobe-Marketing-Cloud/media-sdks/tree/master/samples/launch/js/3.x) |
| [![Chromecast icon](assets/chromecast-icon.png)](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases/tag/chromecast-v3.0.3)<br>[Chromecast SDK 3.x](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases/tag/chromecast-v3.0.3) | [Set up Chromecast for streaming media](/help/implementation/analytics-only/chromecast.md) | [Sample](https://github.com/Adobe-Marketing-Cloud/media-sdks/tree/master/sdks/chromecast/samples/BasicPlayerSample) |
| [![Roku icon](assets/roku-icon.png)](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases/tag/roku-v2.2.7)<br>[Roku SDK 2.x](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases/tag/roku-v2.2.7) | [Set up Roku 2.x for streaming media](/help/implementation/analytics-only/roku-2x.md) | [Sample](https://github.com/Adobe-Marketing-Cloud/media-sdks/tree/master/sdks/roku/samples) |
| [![API icon](assets/api.png)](/help/implementation/media-collection-api/mc-api-overview.md)<br>[Media Collection API](/help/implementation/media-collection-api/mc-api-overview.md) | [Set up Media Collection API](/help/implementation/analytics-only/media-collection-api.md) | |
