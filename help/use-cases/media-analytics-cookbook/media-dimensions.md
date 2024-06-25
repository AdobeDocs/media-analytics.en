---
title: What is Media Stream Attribution?
description: Learn how to link application actions to media tracking data without the need for additional processing rules and custom variables.
exl-id: 75cc9088-776d-4b10-b358-9fff956a7eb7
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Media Stream Attribution {#media-stream-attribution}

With Media Stream Attribution, you can link application actions to media tracking data without the need for additional processing rules and custom variables.

## Media Dimensions Outside Media Tracking

You can add media dimensions to analytics calls such as page views and custom links. During implementation, you must add the media context data parameters to the Analytics track calls. To view the full list of available context data parameters used for media, see [Audio and video parameters.](/help/implementation/variables/audio-video-parameters.md)

To enable this feature for a specific report, re-enable the media tracking configuration from the Admin console.

>[!NOTE]
>
>The media metrics are _not_ available for use outside of media tracking because most of these are computed by the Streaming Media Collection Add-on based on heartbeat events. Also, it is important that the media metrics not be inflated by different implementations.

## Using Media Stream Attribution

The JavaScript example below generates a Custom Link tracking call that has the name set to "Hero Banner".

```javascript
s.contextData["a.media.show"]="Mi Amore"
s.tl(this,'o','Hero Banner');
```

In Analytics reporting, you can use the `Show` eVar to break down the data, and you will be able to count the track link instances. The reporting would look similar to this:

![](/assets/myShow-rpt-1.png)

## Use Cases

The following examples show use cases for the following:

* Category Placement
* Hero Placement
* Engagement
* Subscriptions

![](/assets/vid-stream-attr-category.png)

![](/assets/vid-stream-attr-hero.png)

![](/assets/show-engagement.png)

![](/assets/vid-stream-attr-subs.png)
