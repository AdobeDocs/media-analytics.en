---
title: Learn About Media Analytics SDK End of Support FAQs
description: This topic includes FAQs about the end of support for Media Analytics SDKs.
exl-id: 9601ec17-8421-49d0-9d81-1cfa5e8f37cf
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/qfM2-x6s-SPf4gw2FpLlg7mPI-h-xZ3Y1TeeVALn3fQ
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Media Analytics Mobile SDK End of Support FAQs

With the end of support for Version 4 Mobile SDKs on August 31, 2021, Adobe also ended support for the Media Analytics Mobile SDKs for iOS and Android. (This does not include the Media Analytics SDK for web (JS) and OTT platforms like Chromecast and Roku, which are still supported.) 

This means that Adobe no longer provides fixes, OS-related updates, or support for the Media Analytics Mobile SDK. When migrating to the new Experience Platform SDKs, be aware that the [Media Analytics extensions](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/) must be implemented to enable the Adobe streaming media services.


## Top 5 Things to Know

1. Mobile v4 SDKs are no longer supported as of August 31, 2021. You should migrate to the Adobe Experience Platform (AEP) Mobile SDKs for iOS and Android.

1. An Adobe streaming media services implementation requires the AEP Mobile SDK and use of the Analytics and Media Analytics extensions. As of September 1, 2021, you should use the new AEP Mobile SDKs and extensions.  Media Analytics extensions are configured using Adobe Tags (data collection). For additional information, see [Migrating from Stand-Alone Media SDK to Adobe Launch](/help/legacy/sdk-to-launch/sdk-to-launch-migration.md)

1. Feature development has ended for the Media Analytics SDKs for iOS and Android. New features that were introduced beginning Fall 2019 are enabled using the Media Analytics extensions and the Media Collection API.

1. The Roku and Chromecast SDKs remain available for customer with the Adobe Analytics for Streaming Media Add-on and the Customer Journey Analytics Streaming Media Collection Add-on. The Roku and Chromecast SDKs will continue to be enhanced and supported as stand-alone SDKs. If you use the JS SDK for Media Analytics, you can continue to use the stand-alone SDK or enable the Media Analytics extension using Adobe Data Collection (previously Adobe Launch).

Please reach out to your Adobe Account Team if you have any questions.

## FAQs

1. **Will support for Roku and Chromecast SDKs be impacted?​**

   No.  Roku and Chromecast SDKs will continue to be supported as stand-alone SDKs for the time- being.​
​
1. **Will Media Analytics JS SDK implementations be impacted by this change?​**

   No.  Customers who use the JS SDK for Media Analytics can continue to use the SDK or enable it via Adobe Launch.
​
1. **What is the level of effort to migrate to the Media Analytics extensions?​**

   LOE depends on each customer's implementation, so it will vary.  After reviewing the migration documentation below, please engage consulting and/or customer care for additional support.

    [Media Analytics Extensions: Android migration](/help/legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-android.md)

   [Media Analytics Extensions: iOS migration](/help/legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-ios.md)

   [Media Analytics Extensions: new implementations](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/)

1. **Do I need to have Launch as a tag management system? What if I don't want to use Launch?**

   For the mobile app use case, Launch is not used as a tag management system as it is for web. Using the Launch UI is required for configuring the SDK extensions. This is similar to how you use the Adobe Mobile Services UI to configure the mobile v4 SDK. For installation, the benefit of using Launch is that it gives you customized installation instructions based on the extension you choose.

1. **Does this end of support impact the SDK for tvOS?**

   Yes, for tvOS (version 10+) the recommended implementation is to migrate to the Media Analytics Extensions. For additional information, see [Migrating from the standalone Media SDK to Adobe Launch - iOS](/help/legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-ios.md).

1. **Does this end of support impact the SDK for Fire TV and AndroidTV?​**

   Yes, for Fire TV and AndroidTV, the recommended implementation is to migrate to the Media Analytics Extensions. For additional information, see [Migrating from the standalone Media SDK to Adobe Launch - Android](/help/legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-android.md).
