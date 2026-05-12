---
title: Media Streaming Segments Explained
description: Learn about the reporting segments associated with Media Stream Type including the Segment, Description, and Rule for Media Stream Type.
uuid: 61906b8c-3362-4463-82be-fe0e741a5eb3
exl-id: a450801c-0d6b-4e2a-8662-f00aaaa6e4e0
feature: Streaming Media, Segmentation
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/7RwJQtw-jHlMMV1yc80lUyEYIwIxR-3oh7vN04cPcRg
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
---
# Media Segments{#segments}

Segments allow you to identify subsets of visitors based on characteristics or website interactions. Streaming media segments allow you to identify visitor stream type such as audio, live, or podcast streams. For information about Adobe Analytics segments, see [About segments and containers](https://experienceleague.adobe.com/docs/analytics/components/segmentation/seg-overview.html?lang=en) in the Adobe Analytics Components Guide.

>[!NOTE]
>
>These reporting segments associated with Media Stream Type were introduced on 9/13/18 along with the `streamType` parameter.

|  Segment | Description | Rule |
|---|---|---|
|  Media Stream Type: All |Segment all *media* stream data | "Content (ID) exists" |
|  Media Stream Type: Audio |Segment all *audio* stream data |"Content (ID) exists" AND "Media Stream Type = `audio`" |
|  Media Stream Type: Video |Segment all *video* stream data |"Content (ID) exists" AND "Media Stream Type != `audio`" |
|  Media Content Type: VoD | Segment all VoD contents |"Content Type = `vod`" |
|  Media Content Type: Live | Segment all Live contents |"Content Type = `live`" |
|  Media Content Type: Linear | Segment all Linear contents |"Content Type = `linear`" |
|  Media Content Type: Podcast | Segment all Podcast contents |"Content Type = `podcast`" |
|  Media Content Type: Audiobook | Segment all Audiobook contents |"Content Type = `audiobook`" |
|  Media Content Type: AoD | Segment all AoD contents |"Content Type = `aod`" |
