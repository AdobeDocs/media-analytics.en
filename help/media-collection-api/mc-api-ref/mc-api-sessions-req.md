---
seo-title: Sessions request
title: Sessions request
uuid: 9609192d-4f7f-4fb5-844f-ea89d47c4e30

---

# Sessions request{#sessions-request}

```
POST 
https://{uri}/api/v1/sessions
```

## URI Parameters

None

## Request Body

The request body must be JSON, and must have the same structure as this sample request body: 

```
{ 
    "playerTime": { 
        "playhead": 0, 
        "ts": 1509045324153 
    }, 
    "eventType": "sessionStart", 
    "params": { 
        "media.playerName": "sample-html5-api-player", 
        "analytics.trackingServer": "<your-aa-tracking-server>", 
        "analytics.reportSuite": "<your-aa-rsid>", 
        "analytics.visitorId": "<your-userId>", 
        "media.contentType": "VOD", 
        "media.length": 60.39333333333333, 
        "media.id": "MA API Sample Player", 
        "visitor.marketingCloudOrgId": "<your-org-id>", 
        "media.name": "ClickMe", 
        "media.channel": "sample-channel", 
        "media.sdkVersion": "va-api-0.0.0", 
        "analytics.enableSSL": false 
    }, 
    "customMetadata": { 
        "myCustomData": "<your metadata>", 
        "myCustomData2": "<your metadata>", 
        ... 
    }, 
    "qoeData": { 
        "param1": "<your param-value>", 
        "param2": "<your param-value>", 
        ... 
    } 
}
```

* `playerTime` (Mandatory)
    * `playhead` - Must be in seconds, but it can be a float.
    * `ts` - Timestamp; must be in milliseconds.
* `eventType` (Mandatory)
   **Valid value:** `sessionStart`
* `params` (Mandatory) 
* `customMetadata` (Optional)
* `qoeData` (Optional)

## Response

```
HTTP/1.1 201 Created 
Server: nginx/1.13.5 
Date: Wed, 06 Dec 2017 19:14:51 GMT 
Content-Type: application/octet-stream 
Content-Length: 0 
Location: /api/v1/sessions/bfcca2ca597a3c71bc03b4ce357833ad02b3570d262ecd0c595fcf8f2ae4df58 
Access-Control-Allow-Origin: * 
Access-Control-Allow-Methods: OPTIONS,POST,PUT 
Access-Control-Allow-Headers: Content-Type 
Access-Control-Expose-Headers: Location 
Age: 0 
Via: 1.1 wsg.sanjose08
```

>[!NOTE]
>
>The `/api/v1/` part of the Location header provides the API version. The part of the Location header after `[…]sessions/` is the Session ID.

## Response Codes

|  HTTP Response Code  | Description  |
|---|---|
|  201  | Session created  |
|  400  | Bad Request  |
|  500  | Server error  |

