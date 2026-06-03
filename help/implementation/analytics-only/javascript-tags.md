---
title: Set up the Media Analytics tag extension
description: Use the Adobe Media Analytics (3.x SDK) for Audio and Video tag extension to implement Analytics-only streaming media.
feature: Streaming Media
role: Developer
---
# Set up the Media Analytics tag extension

The Adobe Media Analytics (3.x SDK) for Audio and Video tag extension deploys the Media SDK for JavaScript (3.x) through Tags, with no manual JavaScript installation. This page covers the Tags configuration. To install the SDK in code instead, see [Set up JavaScript for streaming media](javascript.md). For new implementations, consider the recommended [Web SDK tag extension](/help/implementation/edge/web-sdk-tags.md) Edge path.

* **Prerequisites**: Complete the [Analytics-only implementation overview](overview.md).

## Install and configure the extension

Add the Media tracker instance to a tags-enabled site by installing and configuring the extension in the Data Collection UI. For installation and configuration details, see [Adobe Media Analytics (3.x SDK) for Audio and Video extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics-3x/overview.html?lang=en).

## Track media events

With the extension configured, track each media event using its tracker method. See the **Media SDK JS 3.x** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact calls.

## Next step

Once your implementation is complete, you can [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

>[!MORELIKETHIS]
>
>* [Adobe Media Analytics (3.x SDK) for Audio and Video extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/media-analytics-3x/overview.html?lang=en)
>* [Set up JavaScript for streaming media (in code)](javascript.md)
>* [Events overview](/help/implementation/events/overview.md)
