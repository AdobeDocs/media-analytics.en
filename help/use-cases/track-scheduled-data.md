---
title: How to track offline downloaded content in the Streaming Media Collection 
description: Learn how to use the Downloaded Content feature to track media consumption when a user is offline.
uuid: 0718689d-9602-4e3f-833c-8297aae1d909
exl-id: 82d3e5d7-4f88-425c-8bdb-e9101fc1db92
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Upload scheduled data to track live content

You can now upload scheduled data of past live content to more easily and accurately track viewership. 

The following are examples of live content that are supported with scheduled data upload:

* FAST (Free Ad Supported TV) platforms 

* Local streams

Uploading scheduled data allows you to track viewership data for programs that ran during the time you designate in the upload file. You can even gather viewership data for specific topics or program segments. 

These capabilities are available regardless of how you implemented Streaming Media Collection.

## Capabilities

Scheduled data uploads of live content in Streaming Media Collection includes the following capabilities:

* Identify the start and end times of each individual program in the live stream for the period of time that you want to analyze. With accurate start and end times, the precise running time is accurately reflected and can be analyzed against each viewer session.

  For example, precise beginning and end times are not always known for a live sporting event until the event is over. Scheduled data uploads allow you to get accurate reporting by updating the start and end times after the program finishes.

* Create new time-based dimensions for specific topics or program segments (time slots) within a given program. These time-based dimensions allow you to analyze viewership of a program at a more specific level, helping to gather insights about which topics or program segments resonated best.

  For example, when analyzing a live sporting event, such as a soccer match, you can create separate dimensions for the first half, half time, and second half. This allows for more detailed breakdowns of viewer behavior for specific segments of a program.

* Track which programs a person viewed in a given session, or even which topics or program segments the person viewed. You can use this data in Adobe Journey Optimizer to build user journeys for customers who watched a certain program or topic.  


## Prerequisites

Enable Streaming Media Collection on the live content that you want to track, as described in ... <!--specifics??? -->


## Request and fill out the scheduled data file

The scheduled data file is a `.json` file that contains the structure that is required when analyzing scheduled data. This file is available from Adobe through a Customer Care request. 

To request, fill out,and upload the scheduled data file:

1. Request the scheduled data file from Adobe Customer Care.

   1. Log a support ticket with Adobe Customer Care.

   1. Include the following information: ???

      Adobe Customer Care will respond to your request within ____ days. Their response contains a `.json` file that contains the fields you need to fill out.

1. Fill out the scheduled data file that you receive from Adobe Customer Care.

   1. Open the `.json` file that you recieve from Adobe Customer Care
   
   1. Specify the following information:

      * **Matching key**: The channel ID or content ID of the live data that you want to analyze.

      * **Dimension**: 

      * **Start time**: The timestamp of when in the live content you want the analysis to start. <!--what format to include this in?-->

      * **End time**: The timestamp of when in the live content you want the analysis to stop.

        >[!IMPORTANT]
        >
        >If you have multiple scheduled data requests, they cannot have overlapping start and end times.

      * **Additional metadata**: 

1. Send the completed data file to Adobe.

   1. Upload your completed data file to a cloud location, such as an Amazon S3 bucket.
   
   1. Notify Customer Care of the location.

      After your file is uploaded, Adobe Customer Care will run the Analysis and send you the `.json` schema.

1. Match your live data from the time period you specified to the `.json` schema that you receive from Customer Care. <!--what is entailed in this?-->

## Analyze data in Customer Journey Analytics




