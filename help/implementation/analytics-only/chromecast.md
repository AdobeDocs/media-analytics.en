---
title: Set up Chromecast for streaming media
description: Install and configure the Media SDK for Chromecast for Analytics-only streaming media implementations.
feature: Streaming Media
role: Developer
---
# Set up Chromecast for streaming media

The Media SDK for Chromecast sends streaming media data from Chromecast receiver apps directly to Adobe Analytics. The SDK and its documentation are hosted on GitHub.

* **Prerequisites**:
  * Complete the [Analytics-only implementation overview](overview.md).
  * [Download the Media SDK for Chromecast](/help/getting-started/download-sdks.md).

## Install and configure the SDK

Add the SDK to your Chromecast receiver app and configure the tracker as described in the canonical references:

* [Set up the Chromecast SDK](https://github.com/Adobe-Marketing-Cloud/media-sdks/blob/master/docs/2.x/chromecast-setup.md)
* [Chromecast SDK API reference](https://adobe-marketing-cloud.github.io/media-sdks/reference/chromecast/)

## Track media events

With the tracker created, track each media event using its tracker method. See the **Chromecast** tab on each [event](/help/implementation/events/overview.md) and [variable](/help/implementation/variables/overview.md) page for the exact calls.

## Next step

Once your implementation is complete, you can [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

>[!MORELIKETHIS]
>
>* [Chromecast SDK API reference](https://adobe-marketing-cloud.github.io/media-sdks/reference/chromecast/)
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
