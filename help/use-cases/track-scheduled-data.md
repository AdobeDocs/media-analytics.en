---
title: Upload schedule data to track live content 
description: Learn how to upload schedule data to track live content.
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Upload schedule data to track live content

You can upload schedule data of past live Streaming Media content to more easily and accurately track viewership of live content. This includes data for individual programs and even specific topics or program segments.

The following are examples of live content that are supported with schedule data upload:

* FAST (Free Ad Supported TV) platforms 

* Local streams

* Live sports

* News or topical programming

## Capabilities

Schedule data uploads of past live Streaming Media content includes the following capabilities to help analyze program performance: <!-- make this so this reads as these are more examples -->

These capabilities are available regardless of how you implemented Streaming Media Collection.

* **Accurately track program schedules**: Identify the start and end times of each individual program in the live stream for the period of time that you want to analyze. With accurate start and end times, the precise running time is accurately reflected and can be analyzed against each viewer session.

  For example, precise beginning and end times are not always known for a live sporting event until the event is over. Schedule data uploads allow you to get accurate reporting by updating the start and end times after the program finishes.

* **Track individual topics or program segments**: Create new time-based dimensions for specific topics or program segments (time slots) within a given program. These time-based dimensions allow you to analyze viewership of a program at a more specific level, helping to gather insights about which topics or program segments resonated best.

  For example, when analyzing a live sporting event, such as a soccer match, you can create separate dimensions for the first half, half time, and second half. This allows for more detailed breakdowns of viewer behavior for specific segments of a program.

* **Build user journeys in Journey Optimizer**: Track which programs a person viewed in a given session (or even which topics or program segments the person viewed), then use this data in Adobe Journey Optimizer to build user journeys for customers who watched a certain program or who showed interest in a particular topic.  

## How the capability works

The new capability does the following:
1. Reads from the schedule program dataset for schedule program records filtering by the date of the schedule(Only schedule programs for two days in the past, between 48h-24h in the past)
2. Reads from the media dataset all the media close events filtering by date and by the xdm path/value in the schedule program records
3. For each media close event generates as many media schedule start events as shows were overlapping with the media session. Each media schedule start event will have the name and the length of the schedule. Also a new time metric called **scheduleTimePlayed** that will contain the number in seconds the media session overlapped with the scheduled program. The timestamp of the schedule start event will be the timestamp when the show started. 
4. writes in AEP media dataset the new schedule start events

## Prerequisites

To upload schedule data of past live content, you must meet the following prerequisites:

* Streaming Media Collection must be enabled for tracking on the content for which you want to upload schedule data, as described in [Tracking overview](/help/use-cases/track-av-playback/track-core-overview.md). <!--specifics??? -->

* Use Streaming Media Collection with Customer Journey Analytics. This functionality is not available with Adobe Analytics.

* Create Program Schedule Dataset in AEP to push schedule information
   1. Create a schema based on the **Media Analytics Scheduled Program** XDM class  https://github.com/adobe/xdm/blob/master/components/fieldgroups/tv-schedule/media-analytics-scheduled-program.schema.json 
   ![Media Analytics Schedule Program Schema](assets/media_schedule_finish_schema_creation.png)
   1. Create a dataset based on the new schema

* Log a support ticket with Adobe Customer Care with the following information:
   1. Media Dataset - Dataset ID of the dataset where the media sessions data is read from
   1. Schedule Dataset - Dataset ID of the record dataset where the schedule records are pushed
   1. Output Media Dataset - Dataset ID of the dataset where the schedule start events will be saved. This dataset can be identical with the one the Media Dataset. If it is a different one than it should have the same XDM schema as the Media Dataset. 
   1. The organisation id  

## Push schedule information

To push schedule information you should use AEP batch APIs  https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/batch/overview . 
The steps are:
   1. create a json file with the schedule information. The file should contain an array of Schedule Program objects as per XDM schema. 
   1. Upload the file by :
      1. create a new batch and get the batch id from the response
      1. push file with program schedule records using the batch id
      1. complete the batch

   There is a section in this document with curl examples for each call. In the examples we used  the following variables:

    * for authentication with Adobe IO 
      1. CUSTOMER_API_KEY
      1. AUTH_TOKEN 
    * organization id - CUSTOMER_ORG_ID
    * dataset id of the record dataset created in the setup - DATASET_ID
    * batch id created in the first request used in the file upload - BATCH_ID
    * the name of the file used to push records - FILE_NAME

### Example of a schedule json file with two records. The file should contain all scheduled programs for a day. 
   
```
   [
        {
            "_id": "any_identifier_as_id_1",
            "customMetadata": [
                {
                    "name": "Sample value",
                    "value": "Sample value"
                }
            ],
            "defaultMetadata": {
                "album": "Sample value",
                "artist": "Sample value",
                "assetID": "Sample value",
                "author": "Sample value",
                "cdn": "Sample value",
                "dayPart": "Sample value",
                "episode": "Sample value",
                "feed": "Sample value",
                "firstAirDate": "Sample value",
                "firstDigitalDate": "Sample value",
                "genreList": [
                    "Sample value"
                ],
                "label": "Sample value",
                "network": "Sample value",
                "originator": "Sample value",
                "publisher": "Sample value",
                "rating": "Sample value",
                "season": "Sample value",
                "show": "Sample value",
                "showType": "Sample value",
                "station": "Sample value",
                "streamFormat": "Sample value"
            },
            "mediaProgramDetails": {
                "length": 1800,
                "name": "Show Name",
                "startTimestamp": "2025-05-01T00:30:00+00:00"
            },
            "scheduleDate": "2025-05-01",
            "scheduleFilter": {
                "filterPath": "xdm.mediaReporting.sessionDetails.channel",
                "filterValue": "Channel Name"
            },
        },
        {
            "_id": "any_identifier_as_id_2",
            "customMetadata": [
                {
                    "name": "Sample value",
                    "value": "Sample value"
                }
            ],
            "defaultMetadata": {
                "album": "Sample value",
                "artist": "Sample value",
                "assetID": "Sample value",
                "author": "Sample value",
                "cdn": "Sample value",
                "dayPart": "Sample value",
                "episode": "Sample value",
                "feed": "Sample value",
                "firstAirDate": "Sample value",
                "firstDigitalDate": "Sample value",
                "genreList": [
                    "Sample value"
                ],
                "label": "Sample value",
                "network": "Sample value",
                "originator": "Sample value",
                "publisher": "Sample value",
                "rating": "Sample value",
                "season": "Sample value",
                "show": "Sample value",
                "showType": "Sample value",
                "station": "Sample value",
                "streamFormat": "Sample value"
            },
            "mediaProgramDetails": {
                "length": 3600,
                "name": "Show Name 2",
                "startTimestamp": "2025-05-01T01:00:00+00:00"
            },
            "scheduleDate": "2025-05-01",
            "scheduleFilter": {
                "filterPath": "xdm.mediaReporting.sessionDetails.channel",
                "filterValue": "Channel Name"
            }
        }
    ]
```

### Examples of curl calls to push schedule records

   1. Create a new AEP Batch

    ```
        curl -i 'https://platform.adobe.io/data/foundation/import/batches' \
        -X POST \
        -H 'Accept: application/json' \
        -H 'x-api-key: <CUSTOMER_API_KEY>' \
        -H 'x-gw-ims-org-id: <CUSTOMER_ORG_ID>' \
        -H 'Content-Type: application/json' \
        -H 'Authorization: Bearer <OAUTH_TOKEN>' \
        --data-raw '{"datasetId":"<DATASET_ID>","inputFormat":{"format":"json","isMultiLineJson":true},"tags":{"test":["2"]}}'

        HTTP/1.1 201 Created
        {
            "id": "BATCH_ID",
            "imsOrg": "CUSTOMER_ORG_ID",
            "updated": 1749838941763,
            "status": "loading",
            "created": 1749838941763,
            "relatedObjects": [
                {
                    "type": "dataSet",
                    "id": "DATASET_ID"
                }
            ],
            "version": "1.0.0",
            ............
        }
    ```

   1. Push a file with the schedule records

    ```
        curl -i 'https://platform.adobe.io/data/foundation/import/batches/<BATCH_ID>/datasets/<DATASET_ID>/files/<FILE_NAME>' \
        -X PUT \
        -H 'x-api-key: <CUSTOMER_API_KEY>' \
        -H 'x-gw-ims-org-id: <CUSTOMER_ORG_ID>' \
        -H 'Content-Type: application/json' \
        -H 'Authorization: Bearer <OAUTH_TOKEN>' \
        --upload-file ./schedule_21_05_2025.json`
    ```

   1. Complete the batch

    ```
        curl -i 'https://platform.adobe.io/data/foundation/import/batches/<BATCH_ID>?action=COMPLETE' \
        -X POST \
        -H 'x-api-key: <CUSTOMER_API_KEY>' \
        -H 'x-gw-ims-org-id: <CUSTOMER_ORG_ID>' \
        -H 'Content-Type: application/json' \
        -H 'Authorization: Bearer <OAUTH_TOKEN>'
    ```

### What are the schedule program fields:

   1. **mediaProgramDetails** - should contain the minimum information required to create the schedule start event:
      * **startTimestamp** - the time when the show started
      * **name** - the friendly name of the show
      * **length** - the number of seconds the show lasted
        >[!IMPORTANT]
        >
        >If you have multiple schedule data requests, they cannot have overlapping start and end times.
   1. **scheduleDate** - the date on which the show was aired. The format should be YYYY-MM-DD. It is used to filter the schedule dataset and get all the schedules for which adobe will create schedule starts
   1. **scheduleFilter** - used to filter all media session close events
      * **filterPath** - an xdm path to the filled used to filter with
      * **filterValue** - the value used to filter with
   1. **customMetadata** - custom metadata you want to add to the schedule starts events. This metadata will be used overwrite the custom metadata present on the session close events
   1. **defaultMetadata** - specific list of dimensions that can add or overwrite the default medatata present on the media close calls. 
   
   Consider the following examples of dimensions you could create and then report on in Customer Journey Analytics:

        * **["_Episode name_"](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters#episode)**: This dimension could help you learn which episodes in a particular series are performing best.

        * **[Asset ID](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters#asset-id)**



1. Continue with [Analyze data in Customer Journey Analytics](#analyze-data-in-customer-journey-analytics).

## Analyze data in Customer Journey Analytics


Within ___ days of uploading your data file as described in [Request and upload the schedule data file](#request-and-upload-the-schedule-data-file), your data is ready to report on in Customer Journey Analytics.

To report on your past live Streaming Media data in Customer Journey Analytics:

1. Create a new project or open an existing project.

1. Build out the project by creating any tables or visualizations that you need for analyzing your past live Streaming Media data. 

   When building out the project, use the information that you included in the schedule data file and sent to Adobe Customer Care. This includes the matching key, dimensions, and any additional metadata. For more information, see [Request and upload the schedule data file](#request-and-upload-the-schedule-data-file).
   



<!-- 

Extra

Things they need to upload:
Everything on that slide + other metadata
You can't overlap 2 schedules.
You can build a journey in AJO for the people who watch Mike, Mike, and Mike. e.g. 
This is recurring.
Available to all SKUs? "Increases cost for updated data by 22%, but included in the new higher tier Streaming Media SKU."

You can now upload schedule data of past live content to more easily and accurately track viewership. Live content includes content from FAST (Free Ad Supported TV) platforms or local streams.
You can track which programs a person viewed in a given session, or even which topics or program segments they viewed. These capabilities are available regardless of how you implemented Streaming Media Collection.
Previously, it was difficult to accurately tie a given session to specific programs when analyzing live content, and it wasn't possible to tie a given session to individual topics or program segments.
Schedule data uploads of live content in Streaming Media Collection includes the following capabilities:
Upload schedules for past live content, regardless of your Streaming Media Collection implementation.
Identify the start and end times of each individual program in the live stream for the period of time that you want to analyze. With accurate start and end times, the precise running time is accurately reflected and can be analyzed against each viewer session.
For example, precise beginning and end times are not always known for a live sporting event until the event is over. Schedule data uploads allow you to get accurate reporting by updating the start and end times after the program finishes.
Create new time-based dimensions for specific topics or program segments (time slots) within a given program. These time-based dimensions allow you to analyze viewership of a program at a more specific level, helping to gather insights about which topics or program segments resonated best.
For example, when analyzing a live sporting event, such as a soccer match, you can create separate dimensions for the first half, half time, and second half. This allows for more detailed breakdowns of viewer behavior for specific segments of a program.
These capabilities allow you to:
Analyze show viewership to understand performance.
Target users based on program viewership.
Analyze viewership based on metadata like topic, sports league, sponsorship, and so forth.
Target based on metadata viewership.
Correct media metrics for show dimensions of live sports/events for easier analysis at scale.
Increased ease of use for live sports

-->
