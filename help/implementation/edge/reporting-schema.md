---
title: XDM reporting schema
description: Learn which Media Edge API events generate Experience Events in Adobe Experience Platform and how to validate your implementation using the mediaReporting XDM schema.
feature: Streaming Media
role: User, Admin, Developer
exl-id: c3a4d31b-8f9e-4d7a-9b2e-1a5f0e8c7d39
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
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
---

# XDM reporting schema

When you send media tracking events using the Adobe Experience Platform Edge Network, the Media Analytics backend processes those events and writes computed Experience Events to Platform datasets. Understanding which events reach Platform, and what the backend computes for you, helps you validate your implementation and build accurate reports in Customer Journey Analytics or Adobe Analytics.

Two distinct XDM schemas are used in different parts of the collection and reporting pipeline:

| Schema | Namespace | Direction | Purpose |
|---|---|---|---|
| Media Collection | `xdm.mediaCollection` | Client &rarr; Adobe | What your player sends for each tracking event. Used by [variables](/help/implementation/variables/). |
| Media Reporting | `xdm.mediaReporting` | Adobe &rarr; Platform | What the backend writes to datasets after processing. Used by [dimensions](/help/reporting/dimensions/overview.md) and [metrics](/help/reporting/metrics/overview.md). |

Fields present in `mediaReporting` but absent from the `mediaCollection` payload are derived from the full sequence of events in a session. You never send these fields; Adobe generates them.

## Events that write to Platform datasets

Of the 12 trackable event types, only five generate individual Experience Event writes to datasets:

| Event type | Included in datasets | Notes |
|---|---|---|
| [Session start](/help/implementation/events/session/session-start.md) | Yes | Written when the session is initialized |
| [Ad start](/help/implementation/events/ads/ad-start.md) | Yes | Written when an individual ad begins |
| [Ad complete](/help/implementation/events/ads/ad-complete.md) | Yes | Written when an ad plays to completion |
| [Chapter complete](/help/implementation/events/chapters/chapter-complete.md) | Yes | Written when a chapter plays to completion |
| [Session complete](/help/implementation/events/session/session-complete.md) | Yes | Written when the session ends; richest computed field set |
| [Play](/help/implementation/events/playback/play.md) | No | Used to compute `timePlayed` |
| [Pause start](/help/implementation/events/playback/pause-start.md) | No | Used to compute `pauseCount` and `pauseTime` |
| [Ping](/help/implementation/events/playback/ping.md) | No | Heartbeat; used to detect session inactivity |
| [Buffer start](/help/implementation/events/playback/buffer-start.md) | No | Used to compute QoE buffer metrics |
| [Bitrate change](/help/implementation/events/playback/bitrate-change.md) | No | Used to compute QoE bitrate metrics |
| [State start](/help/implementation/events/player-state/state-start.md) | No | Used to compute player state metrics |
| [Error](/help/implementation/events/error.md) | No | Used to compute `errorCount` in QoE |

## Backend-computed fields

The following fields appear in `mediaReporting` payloads but are never part of the collection payload. The backend derives them from the full event sequence.

**Session-level** (appear on `sessionComplete`):

| Field | Description |
|---|---|
| `xdm.mediaReporting.sessionDetails.timePlayed` | Total seconds of main content played, excluding ads |
| `xdm.mediaReporting.sessionDetails.totalTimePlayed` | Total seconds elapsed, including ads |
| `xdm.mediaReporting.sessionDetails.uniqueTimePlayed` | Deduplicated seconds. Intervals viewed more than once are counted only once |
| `xdm.mediaReporting.sessionDetails.averageMinuteAudience` | `timePlayed` divided by content length |
| `xdm.mediaReporting.sessionDetails.estimatedStreams` | Estimated concurrent streams |
| `xdm.mediaReporting.sessionDetails.adCount` | Number of ads that started |
| `xdm.mediaReporting.sessionDetails.chapterCount` | Number of chapters that started |
| `xdm.mediaReporting.sessionDetails.pauseCount` / `xdm.mediaReporting.sessionDetails.pauseTime` | Pause frequency and total pause duration |
| `xdm.mediaReporting.sessionDetails.hasProgress10` … `xdm.mediaReporting.sessionDetails.hasProgress95` | Progress milestone flags (10%, 25%, 50%, 75%, 95%) |
| `xdm.mediaReporting.sessionDetails.hasSegmentView` | Whether at least one frame of content was viewed |
| `xdm.mediaReporting.sessionDetails.isCompleted` / `xdm.mediaReporting.sessionDetails.isPlayed` | Completion and start flags |
| `xdm.mediaReporting.sessionDetails.secondsSinceLastCall` | Time between last ping and session close |
| `xdm.mediaReporting.sessionDetails.segment` | Content segment bracket (e.g., `[0-1]`) |

**Ad-level** (appear on `adComplete`):

| Field | Description |
|---|---|
| `xdm.mediaReporting.advertisingDetails.timePlayed` | Seconds of ad content played |
| `xdm.mediaReporting.advertisingDetails.isCompleted` | Whether the ad played to completion |

**Chapter-level** (appear on `chapterComplete`):

| Field | Description |
|---|---|
| `xdm.mediaReporting.chapterDetails.timePlayed` | Seconds of chapter content played |
| `xdm.mediaReporting.chapterDetails.isCompleted` | Whether the chapter played to completion |
| `xdm.mediaReporting.chapterDetails.isStarted` | Whether the chapter started |

**QoE** (aggregated on `sessionComplete`):

| Field | Description |
|---|---|
| `xdm.mediaReporting.qoeDataDetails.bitrateAverage` | Average bitrate across the session |
| `xdm.mediaReporting.qoeDataDetails.bitrateAverageBucket` | Bucketed average bitrate range |
| `xdm.mediaReporting.qoeDataDetails.bitrateChangeCount` | Number of bitrate changes |
| `xdm.mediaReporting.qoeDataDetails.errorCount` | Number of errors |
| `xdm.mediaReporting.qoeDataDetails.droppedFrames` | Total dropped frames |
| `xdm.mediaReporting.qoeDataDetails.playerSdkErrors` | Array of player error codes |
| `xdm.mediaReporting.qoeDataDetails.hasErrorImpactedStreams` | Whether any error occurred |
| `xdm.mediaReporting.qoeDataDetails.hasDroppedFrameImpactedStreams` | Whether dropped frames occurred |
| `xdm.mediaReporting.qoeDataDetails.hasBitrateChangeImpactedStreams` | Whether bitrate changes occurred |

## Downloaded content

For sessions tracked using the [downloaded endpoint](/help/use-cases/track-downloaded-content.md), the backend automatically sets `xdm.mediaReporting.sessionDetails.isDownloaded` to `true` on the `sessionStart` reporting event. All other reporting events for downloaded sessions follow the same schema as live sessions. Use this field in CJA or Adobe Analytics to filter or segment downloaded playback.

See [Downloaded endpoint](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/downloaded/) in the Media Edge API reference for collection implementation details.

## Validate your implementation

After sending events through the Media Edge API, verify your data landed correctly using one of the following methods:

**Adobe Experience Platform dataset preview**

1. In [CX Enterprise](https://experience.adobe.com), navigate to **[!UICONTROL Datasets]** and select your streaming media dataset.
2. Select **[!UICONTROL Preview dataset]** to see the most recently ingested Experience Events.
3. Confirm that `eventType` values such as `media.sessionStart` and `media.sessionComplete` appear with populated `mediaReporting` fields.

**Customer Journey Analytics dataset inspection**

1. In CJA, open the connection associated with your streaming media dataset.
2. Select **Add datasets** and inspect the schema to confirm the `mediaReporting` fields are mapped to the expected dimensions and metrics.

**Adobe Analytics processing rules (if using Analytics destination)**

For Adobe Analytics report suites receiving data via the Analytics source connector, you can use Processing Rules to map `mediaReporting` context data variables to custom props or eVars. The `isDownloaded` flag is available as `a.media.downloaded`.

## XDM payload examples

The following examples show the complete `mediaReporting` XDM structure for each reporting event as written to Platform datasets. The `_{tenantName}` property represents your organization's tenant namespace for any custom fields.

+++media.sessionStart

```json
{
  "xdm": {
    "_{tenantName}": {
      "customField1": "c1",
      "customField2": "c2"
    },
    "mediaReporting": {
      "sessionDetails": {
        "adLoad": "adLoadType",
        "appVersion": "sdk-1.0",
        "artist": "test-artist",
        "channel": "broadcastChannel",
        "rating": "4.8/5",
        "show": "test-name Series",
        "genreList": ["Comedy"],
        "episode": "4933",
        "originator": "Tokala Clementine",
        "isViewed": true,
        "network": "test-network",
        "firstAirDate": "firstAirDate",
        "streamType": "video",
        "authorized": "true",
        "streamFormat": "streamFormat",
        "genre": "Comedy",
        "station": "test-station",
        "hasResume": false,
        "season": "1521",
        "showType": "sitcom",
        "ID": "cd7b[...]6f",
        "contentType": "VOD",
        "friendlyName": "test-friendly-name",
        "playerName": "HTML5 player",
        "album": "test-album",
        "author": "test-author",
        "length": 100,
        "dayPart": "dayPart",
        "label": "test-label",
        "mvpd": "test-mvpd",
        "feed": "sourceFeed",
        "assetID": "/uri-reference",
        "name": "test-name",
        "publisher": "test-media-publisher",
        "firstDigitalDate": "releaseDate"
      }
    },
    "implementationDetails": {
      "environment": "server",
      "name": "https://ns.adobe.com/experience/edge",
      "version": "0.0.0"
    },
    "identityMap": {
      "ECID": [
        {
          "id": "5191[...]21",
          "authenticatedState": "ambiguous",
          "primary": true
        }
      ]
    },
    "eventType": "media.sessionStart",
    "_id": "0[...]0",
    "timestamp": "YYYY-11-20T12:43:35Z"
  }
}
```

+++

+++media.adStart

```json
{
  "xdm": {
    "_{tenantName}": {
      "customField1": "c1",
      "customField2": "c2"
    },
    "environment": {
      "browserDetails": {},
      "ipV4": "130.248.81.10"
    },
    "mediaReporting": {
      "advertisingDetails": {
        "advertiser": "Adobe Marketing",
        "podPosition": 1,
        "placementID": "placementID",
        "example": "https://example.com",
        "playerName": "HTML5 player",
        "campaignID": "Adobe Analytics",
        "name": "/uri-reference/001",
        "length": 10,
        "siteID": "siteID",
        "isStarted": true,
        "creativeID": "creativeID",
        "friendlyName": "Ad 1"
      },
      "sessionDetails": {
        "adLoad": "adLoadType",
        "appVersion": "sdk-1.0",
        "artist": "test-artist",
        "pev3": "videoAd",
        "channel": "broadcastChannel",
        "rating": "4.8/5",
        "show": "test-name Series",
        "genreList": ["Comedy"],
        "episode": "4933",
        "originator": "Tokala Clementine",
        "network": "test-network",
        "firstAirDate": "firstAirDate",
        "streamType": "video",
        "pccr": true,
        "authorized": "true",
        "streamFormat": "streamFormat",
        "genre": "Comedy",
        "station": "test-station",
        "season": "1521",
        "showType": "sitcom",
        "ID": "cd7b[...]6f",
        "contentType": "VOD",
        "friendlyName": "test-friendly-name",
        "playerName": "HTML5 player",
        "album": "test-album",
        "author": "test-author",
        "length": 100,
        "dayPart": "dayPart",
        "label": "test-label",
        "mvpd": "test-mvpd",
        "feed": "sourceFeed",
        "assetID": "/uri-reference",
        "name": "test-name",
        "publisher": "test-media-publisher",
        "firstDigitalDate": "releaseDate"
      },
      "advertisingPodDetails": {
        "offset": 0,
        "ID": "3d594614f445f6b00014e9b77730b833_1",
        "friendlyName": "Mid-ad"
      }
    },
    "implementationDetails": {
      "environment": "server",
      "name": "https://ns.adobe.com/experience/edge",
      "version": "0.0.0"
    },
    "identityMap": {
      "ECID": [
        {
          "id": "5191[...]21",
          "authenticatedState": "ambiguous",
          "primary": true
        }
      ]
    },
    "eventType": "media.adStart",
    "_id": "d[...]0",
    "timestamp": "YYYY-11-20T12:43:56Z"
  }
}
```

+++

+++media.adComplete

```json
{
  "xdm": {
    "_{tenantName}": {
      "customField1": "c1",
      "customField2": "c2"
    },
    "mediaReporting": {
      "advertisingDetails": {
        "advertiser": "Adobe Marketing",
        "podPosition": 1,
        "placementID": "placementID",
        "example": "https://example.com",
        "playerName": "HTML5 player",
        "campaignID": "Adobe Analytics",
        "length": 10,
        "creativeID": "creativeID",
        "timePlayed": 7,
        "name": "/uri-reference/001",
        "siteID": "siteID",
        "friendlyName": "Ad 1",
        "isCompleted": true
      },
      "sessionDetails": {
        "adLoad": "adLoadType",
        "appVersion": "sdk-1.0",
        "artist": "test-artist",
        "pev3": "videoAd",
        "channel": "broadcastChannel",
        "rating": "4.8/5",
        "show": "test-name Series",
        "genreList": ["Comedy"],
        "episode": "4933",
        "originator": "Tokala Clementine",
        "network": "test-network",
        "firstAirDate": "firstAirDate",
        "streamType": "video",
        "pccr": true,
        "authorized": "true",
        "streamFormat": "streamFormat",
        "genre": "Comedy",
        "station": "test-station",
        "season": "1521",
        "showType": "sitcom",
        "ID": "cd7b[...]6f",
        "contentType": "VOD",
        "friendlyName": "test-friendly-name",
        "playerName": "HTML5 player",
        "album": "test-album",
        "author": "test-author",
        "length": 100,
        "dayPart": "dayPart",
        "label": "test-label",
        "mvpd": "test-mvpd",
        "feed": "sourceFeed",
        "assetID": "/uri-reference",
        "name": "test-name",
        "publisher": "test-media-publisher",
        "firstDigitalDate": "releaseDate"
      },
      "advertisingPodDetails": {
        "offset": 0,
        "ID": "3d594614f445f6b00014e9b77730b833_1",
        "friendlyName": "Mid-ad"
      }
    },
    "implementationDetails": {
      "environment": "server",
      "name": "https://ns.adobe.com/experience/edge",
      "version": "0.0.0"
    },
    "identityMap": {
      "ECID": [
        {
          "id": "5191[...]21",
          "authenticatedState": "ambiguous",
          "primary": true
        }
      ]
    },
    "eventType": "media.adComplete",
    "_id": "f[...]0",
    "timestamp": "YYYY-11-20T12:44:03Z"
  }
}
```

+++

+++media.chapterComplete

```json
{
  "xdm": {
    "_{tenantName}": {
      "customField1": "c1",
      "customField2": "c2",
      "customTest": "myCustomValue1"
    },
    "environment": {
      "browserDetails": {},
      "ipV4": "130.248.81.10"
    },
    "mediaReporting": {
      "sessionDetails": {
        "adLoad": "adLoadType",
        "appVersion": "sdk-1.0",
        "artist": "test-artist",
        "pev3": "video",
        "channel": "broadcastChannel",
        "rating": "4.8/5",
        "show": "test-name Series",
        "genreList": ["Comedy"],
        "episode": "4933",
        "originator": "Tokala Clementine",
        "network": "test-network",
        "firstAirDate": "firstAirDate",
        "streamType": "video",
        "pccr": true,
        "authorized": "true",
        "streamFormat": "streamFormat",
        "genre": "Comedy",
        "station": "test-station",
        "season": "1521",
        "showType": "sitcom",
        "ID": "cd7b[...]6f",
        "contentType": "VOD",
        "friendlyName": "test-friendly-name",
        "playerName": "HTML5 player",
        "album": "test-album",
        "author": "test-author",
        "length": 100,
        "dayPart": "dayPart",
        "label": "test-label",
        "mvpd": "test-mvpd",
        "feed": "sourceFeed",
        "assetID": "/uri-reference",
        "name": "test-name",
        "publisher": "test-media-publisher",
        "firstDigitalDate": "releaseDate"
      },
      "chapterDetails": {
        "timePlayed": 10,
        "offset": 0,
        "length": 10,
        "index": 1,
        "ID": "3d594614f445f6b00014e9b77730b833_1",
        "isStarted": true,
        "friendlyName": "Chapter 1",
        "isCompleted": true
      }
    },
    "implementationDetails": {
      "environment": "server",
      "name": "https://ns.adobe.com/experience/edge",
      "version": "0.0.0"
    },
    "identityMap": {
      "ECID": [
        {
          "id": "5191[...]21",
          "authenticatedState": "ambiguous",
          "primary": true
        }
      ]
    },
    "eventType": "media.chapterComplete",
    "_id": "a[...]0",
    "timestamp": "YYYY-11-20T12:44:24Z"
  }
}
```

+++

+++media.sessionComplete

```json
{
  "xdm": {
    "_{tenantName}": {
      "customField1": "c1",
      "customField2": "c2"
    },
    "environment": {
      "browserDetails": {},
      "ipV4": "130.248.81.10"
    },
    "mediaReporting": {
      "qoeDataDetails": {
        "playerSdkErrors": ["test-buffer-start"],
        "bitrateAverageBucket": "0-99",
        "bitrateChangeCount": 1,
        "droppedFrames": 30,
        "hasErrorImpactedStreams": true,
        "hasBitrateChangeImpactedStreams": true,
        "hasDroppedFrameImpactedStreams": true,
        "bitrateAverage": 35,
        "timeToStart": 1,
        "errorCount": 1
      },
      "sessionDetails": {
        "adLoad": "adLoadType",
        "appVersion": "sdk-1.0",
        "hasProgress10": true,
        "pev3": "video",
        "channel": "broadcastChannel",
        "rating": "4.8/5",
        "episode": "4933",
        "pauseTime": 3,
        "streamType": "video",
        "pccr": true,
        "authorized": "true",
        "segment": "[0-1]",
        "season": "1521",
        "showType": "sitcom",
        "pauseCount": 1,
        "ID": "cd7b[...]6f",
        "contentType": "VOD",
        "uniqueTimePlayed": 47,
        "totalTimePlayed": 55,
        "author": "test-author",
        "hasProgress25": true,
        "feed": "sourceFeed",
        "timePlayed": 48,
        "name": "test-name",
        "publisher": "test-media-publisher",
        "hasPauseImpactedStreams": true,
        "averageMinuteAudience": 0.48,
        "artist": "test-artist",
        "show": "test-name Series",
        "genreList": ["Comedy"],
        "originator": "Tokala Clementine",
        "network": "test-network",
        "firstAirDate": "firstAirDate",
        "hasSegmentView": true,
        "streamFormat": "streamFormat",
        "genre": "Comedy",
        "station": "test-station",
        "friendlyName": "test-friendly-name",
        "isCompleted": true,
        "playerName": "HTML5 player",
        "album": "test-album",
        "chapterCount": 1,
        "length": 100,
        "adCount": 1,
        "dayPart": "dayPart",
        "label": "test-label",
        "mvpd": "test-mvpd",
        "secondsSinceLastCall": 51,
        "assetID": "/uri-reference",
        "isPlayed": true,
        "estimatedStreams": 1,
        "firstDigitalDate": "releaseDate"
      },
      "states": [
        {
          "isSet": true,
          "name": "mute",
          "count": 1,
          "time": 3
        },
        {
          "isSet": true,
          "name": "pictureInPicture",
          "count": 1,
          "time": 3
        }
      ]
    },
    "implementationDetails": {
      "environment": "server",
      "name": "https://ns.adobe.com/experience/edge",
      "version": "0.0.0"
    },
    "identityMap": {
      "ECID": [
        {
          "id": "5191[...]21",
          "authenticatedState": "ambiguous",
          "primary": true
        }
      ]
    },
    "eventType": "media.sessionComplete",
    "_id": "a[...]0",
    "timestamp": "YYYY-11-20T12:44:40Z"
  }
}
```

+++

+++media.sessionStart (downloaded content)

Sessions tracked using the [downloaded endpoint](/help/use-cases/track-downloaded-content.md) follow the same reporting schema with one key difference: `xdm.mediaReporting.sessionDetails.isDownloaded` is set to `true` on the `sessionStart` reporting event. All other event types are identical to the live content examples above.

```json
{
  "xdm": {
    "mediaReporting": {
      "customMetadata": [
        {
          "name": "customData",
          "value": "example"
        }
      ],
      "playhead": 0,
      "sessionDetails": {
        "ID": "d8a25708a6b0be83975e32e2f422105ed62f51ff67e6d82d898657534ab9244f",
        "channel": "channel",
        "contentType": "VOD",
        "length": 100,
        "name": "123456789",
        "playerName": "playerName",
        "isDownloaded": true
      }
    },
    "eventType": "media.sessionStart",
    "timestamp": "YYYY-09-26T15:52:24Z",
    "identityMap": {
      "ECID": [
        {
          "id": "51910389753901685456014889838591030721"
        }
      ]
    },
    "implementationDetails": {
      "version": "0.0.1",
      "environment": "browser",
      "name": "https://ns.adobe.com/experience/edge"
    }
  }
}
```

+++
