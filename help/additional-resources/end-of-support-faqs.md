---
title: Learn About Media Analytics SDK End of Support FAQs
description: This topic includes FAQs about the end of support for Media Analytics SDKs.
exl-id: 9601ec17-8421-49d0-9d81-1cfa5e8f37cf
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Media Analytics Mobile SDK End of Support FAQs

With the end of support for Version 4 Mobile SDKs on August 31, 2021, Adobe also ended support for the Media Analytics Mobile SDKs for iOS and Android. (This does not include the Media Analytics SDK for web (JS) and OTT platforms like Chromecast and Roku, which are still supported.) 

This means that Adobe no longer provides fixes, OS-related updates, or support for the Media Analytics Mobile SDK. When migrating to the new Experience Platform SDKs, be aware that the [Media Analytics extensions](https://developer.adobe.com/client-sdks/documentation/adobe-media-analytics/) must be implemented to enable the Adobe Streaming Media Collection.


## Top 5 Things to Know

1. Mobile v4 SDKs are no longer supported as of August 31, 2021. You should migrate to the Adobe Experience Platform (AEP) Mobile SDKs for iOS and Android.

1. Analytics for Streaming Media implementation requires the AEP Mobile SDK and use of the Analytics and Media Analytics extensions. As of September 1, 2021, you should use the new AEP Mobile SDKs and extensions.  Media Analytics extensions are configured using Adobe Tags (data collection). For additional information, see [Migrating from Stand-Alone Media SDK to Adobe Launch](/help/legacy/sdk-to-launch/sdk-to-launch-migration.md)

1. Feature development has ended for the Media Analytics SDKs for iOS and Android. New features that were introduced beginning Fall 2019 are enabled using the Media Analytics extensions and the Media Collection API.

1. The Roku and Chromecast SDKs remain available for Analytics for Streaming Media customers. The Roku and Chromecast SDKs will continue to be enhanced and supported as stand-alone SDKs. If you use the JS SDK for Media Analytics, you can continue to use the stand-alone SDK or enable the Media Analytics extension using Adobe Data Collection (previously Adobe Launch).

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
