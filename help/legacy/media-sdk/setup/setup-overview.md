---
title: Implement Media SDKs Explained
description: "Learn how to set up the Media SDK for media tracking in your mobile, OTT, and browser (JS) applications."
uuid: 06fefedb-b0c8-4f7d-90c8-e374cdde1695
exl-id: a175332e-0bdc-44aa-82cb-b3f879e7abfc
feature: Media Analytics
role: User, Admin, Data Engineer
---
# Legacy - Media SDK Setup Overview {#setup-overview}

After you download the Media SDK for your video app or player, follow the information in this section to setup and implement the Media SDK.


## General Implementation Guidelines {#general-implementation-guidelines}

There are three main SDK components used in tracking with the Streaming Media Collection:
* Media Heartbeat Config—The `MediaHeartbeatConfig` contains the basic settings for reporting.
* Media Heartbeat Delegate—The `MediaHeartbeatDelegate` controls playback time and the QoS object.
* Media Heartbeat—The `MediaHeartbeat` is the primary library containing members and methods.

## Implement the Streaming Media SDK

To setup and use the Streaming Media SDK, complete the following implementation steps:

1. Create a `MediaHeartbeatConfig` instance and set your configuration parameter values.

   |  &nbsp;Variable Name&nbsp; | Description&nbsp; | Required | &nbsp;Default Value&nbsp; |
   |---|---|:---:|---|
   |  `trackingServer`  | Tracking server for media analytics. This is different from your analytics tracking server. | Yes | Empty String |
   |  `channel`  | Channel name  | No  | Empty String  |
   |  `ovp`  | Name of the online media platform through which content gets distributed  | No  | Empty String  |
   |  `appVersion`  | Version of the media player app/SDK  | No  | Empty String  |
   |  `playerName`  | Name of the media player in use, i.e., "AVPlayer", "HTML5 Player", "My Custom Player"  | No  | Empty String  |
   |  `ssl`  | Indicates whether calls should be made over HTTPS  | No  | false  |
   |  `debugLogging`  | Indicates whether debug logging is enabled  | No  | false  |

1. Implement the `MediaHeartbeatDelegate`.

    | &nbsp;Method name&nbsp; | &nbsp;Description&nbsp; | Required |
    | --- | --- | :---: |
    | `getQoSObject()` | Returns the `MediaObject` instance that contains the current QoS information. This method will be called multiple times during a playback session. Player implementation must always return the most recently available QoS data.  | Yes |
    | `getCurrentPlaybackTime()` | Returns the current position of the playhead. <br /> For VOD tracking, the value is specified in seconds from the beginning of the media item. <br /> For live streaming, if the player does not provide information about the content duration, the value can be specified as the number of seconds since midnight UTC of that day. <br /> Note: When using progress markers, the content duration is required and the playhead needs to be updated as number of seconds from the beginning of the media item, starting with 0. | Yes |

   >[!TIP]
   >
   >The Quality of Service (QoS) object is optional. If QoS data is available for your player and you wish to track that data, then the following variables are required:

   |  Variable name  | Description&nbsp;&nbsp;  | Required  |
   | --- | --- | :---: |
   |  `bitrate`  | The bitrate of media in bits per second.  | Yes  |
   |  `startupTime`  | The start up time of media in milliseconds.  | Yes  |
   |  `fps`  | The frames displayed per second.  | Yes  |
   |  `droppedFrames`  | The number of dropped frames so far.  | Yes  |

1. Create the `MediaHeartbeat` instance.

   Use the `MediaHertbeatConfig` and `MediaHertbeatDelegate` to create the `MediaHeartbeat` instance.

   >[!IMPORTANT]
   >
   >Make sure that your `MediaHeartbeat` instance is accessible and does not get deallocated until the end of the session. This instance will be used for all the following media tracking events.

   >[!TIP]
   >
   >`MediaHeartbeat` requires an instance of `AppMeasurement` to send calls to Adobe Analytics.

1. Combine all of the pieces.

   The following sample code utilizes our JavaScript 2.x SDK for an HTML5 video player:

   ```javascript
   // Create local references to the heartbeat classes
   var MediaHeartbeat = ADB.va.MediaHeartbeat;
   var MediaHeartbeatConfig = ADB.va.MediaHeartbeatConfig;
   var MediaHeartbeatDelegate = ADB.va.MediaHeartbeatDelegate;

   //Media Heartbeat Config
   var mediaConfig = new MediaHeartbeatConfig();
   mediaConfig.trackingServer = "[your_namespace].hb.omtrdc.net";
   mediaConfig.playerName = "HTML5 Basic";
   mediaConfig.channel = "Video Channel";
   mediaConfig.debugLogging = true;
   mediaConfig.appVersion = "2.0";
   mediaConfig.ssl = false;
   mediaConfig.ovp = "";

   // Media Heartbeat Delegate
   var mediaDelegate = new MediaHeartbeatDelegate();

   // Set mediaDelegate CurrentPlaybackTime
   mediaDelegate.getCurrentPlaybackTime = function() {
       return video.currentTime;
   };

   // Set mediaDelegate QoSObject - OPTIONAL
   mediaDelegate.getQoSObject = function() {
       return MediaHeartbeat.createQoSObject(video.bitrate,  
                                             video.startuptime,  
                                             video.fps,  
                                             video.droppedframes);
   }
   // Create mediaHeartbeat instance      
   this.mediaHeartbeat =  
     new MediaHeartbeat(mediaDelegate, mediaConfig, appMeasurementInstance);  
   ```

## Validate {#validate}

Media Analytics tracking implementations generate two types of tracking calls:

* Media and ad Start calls are sent directly to the Adobe Analytics (AppMeasurement) server.
* Heartbeat calls are sent to the Media Analytics (heartbeats) tracking server, processed there, and passed on to the Adobe Analytics server.

* **Adobe Analytics (AppMeasurement) server**
   For more information about tracking server options, see [Correctly populate the trackingServer and trackingServerSecure variables.](https://helpx.adobe.com/analytics/kb/determining-data-center.html)

  >[!IMPORTANT]
  >
  >An RDC tracking server or CNAME resolving to an RDC server is required for Experience Cloud Visitor ID service.

  The analytics tracking server should end in "`.sc.omtrdc.net`" or be a CNAME.

* ** Media Analytics (Heartbeats) server**
   This always has the format "`[your_namespace].hb.omtrdc.net`". The value of "`[your_namespace]`" specifies your company, and is provided by Adobe.

Media tracking works the same across all platforms, desktop and mobile. Audio tracking currently works on mobile platforms. For all tracking calls there are a few key universal variables to be validated:
