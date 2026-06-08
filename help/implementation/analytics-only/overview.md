---
title: Analytics-only implementation overview
description: Prerequisites and implementation methods for the Adobe Analytics for Streaming Media add-on, used for Analytics-only implementations.
feature: Streaming Media
role: User, Admin, Developer
---
# Analytics-only implementation overview

Analytics-only implementations use the Adobe Analytics for Streaming Media add-on to send data directly to Adobe Analytics, without the Edge Network. These methods remain fully supported. For new implementations, Adobe recommends the [Edge implementation](/help/implementation/edge/overview.md) instead, because it makes data available to Customer Journey Analytics, Adobe Journey Optimizer, and Real-Time CDP in addition to Adobe Analytics.

## Prerequisites

1. **Complete the general prerequisites.** See the [general prerequisites](/help/getting-started/prereqs.md).

1. **Confirm an Adobe Analytics implementation.** An Analytics-only streaming media implementation requires a basic Adobe Analytics implementation. See [Implement Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html).

1. **Obtain the media tracking server URL.** Ask your Adobe Analytics representative for the media tracking server URL (the `collection-api-server` URL). The domain typically follows the pattern `[your_namespace].hb-api.omtrdc.net`.

1. **Download the SDK or install the extension.** Depending on your platform, [download the current SDK](/help/getting-started/download-sdks.md) or install the required tag extension.

## Choose your implementation method

Each page covers the streaming-media-specific setup. The per-event and per-variable code lives in [Events](/help/implementation/events/overview.md) and [Variables](/help/implementation/variables/overview.md).

| Codebase | In-code | Using Tags |
|---|---|---|
| Web (JavaScript) | [JavaScript](javascript.md) | [Media Analytics tag extension](javascript-tags.md) |
| Chromecast | [Chromecast](chromecast.md) | — |
| Roku | [Roku 2.x](roku-2x.md) | — |
| API | [Media Collection API](media-collection-api.md) | — |

## Next step

Once your implementation is complete, you can [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

>[!MORELIKETHIS]
>
>* [Implementation overview](/help/implementation/overview.md)
>* [Events overview](/help/implementation/events/overview.md)
>* [Variables overview](/help/implementation/variables/overview.md)
