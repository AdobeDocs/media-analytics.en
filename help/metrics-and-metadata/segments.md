---
seo-title: Segments
title: Segments
uuid: 61906b8c-3362-4463-82be-fe0e741a5eb3

---

# Segments{#segments}

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

