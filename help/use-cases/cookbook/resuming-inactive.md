---
title: Resuming Inactive Sessions
description: Learn how to handle resuming an inactive session.
uuid: 3ff1205d-7bbe-4016-9bd7-6e34b7862c4c
exl-id: ee4cf7f5-5788-4d35-a04d-4ed714ccd663
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/KT7NfrYlagrMwAjsrbSNR8YUbj5d-ihU8AfJ6wcbgOA
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
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
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Resuming inactive sessions{#resuming-inactive-sessions}

## Long Pauses

The Media SDK automatically tracks how long the media playback is in one of the following inactive states:

* Paused
* Seeking
* Stalled
* Buffering

If a media tracking session remains in an inactive state for longer than 30 minutes, the session will automatically be closed. If the user resumes after a previously inactive video tracking session (`trackPlay`), Media Heartbeat automatically creates a new video session using the previously used video information and metadata, and sends a resume heartbeat event.

## Cross-device handoff using the resume flag

The same resume mechanism that handles single-app session continuation also applies when a viewer transfers playback between devices — for example, casting a video from a mobile phone to a TV or Chromecast receiver. Because each device runs its own Media SDK instance, the handoff creates multiple sessions by default. Use the resume flag to stitch them into a logical continuation so that Analytics reports the combined viewing as a single piece of engagement rather than separate media starts.

**How to implement:**

1. On the **source device** (e.g., the phone), call `trackSessionEnd` when the viewer initiates the cast. Do not call `trackComplete` — the content is not finished, it is moving to another device.
2. On the **destination device** (e.g., the Chromecast), call `trackSessionStart` with the resume flag set to `true` and the same content metadata (name, ID, length) used on the source device. Pass the playhead position where the viewer left off on the source device.
3. If the viewer later returns playback to the source device, repeat the same pattern: `trackSessionEnd` on the destination and `trackSessionStart` with the resume flag on the source.

Setting the resume flag causes Adobe Analytics to increment [Content resumes](/help/reporting/metrics/content-resumes.md) rather than [Media starts](/help/reporting/metrics/media-starts.md) for the second and subsequent legs of the handoff. Because there is no built-in mechanism to share the session ID between SDK instances, the resume flag is a client-side declaration — you pass it based on your application logic when you know the viewer is continuing a previous session.

## Manually resume previously closed session

The Media SDK will only automatically resume sessions if the application was not closed. If the application stores user data and has the capability to resume a previously closed media, it is possible to manually trigger a resume event. When starting the video tracking session, set the optional Video Resumed property.

### Android

```java
// Set MediaHeartbeat.MediaObjectKey.mediaResumed to true
public void onmediaLoad(Observable observable, Object data) {

  // Replace <MEDIA_NAME> with the media name.
  // Replace <MEDIA_ID> with a media unique identifier.
  // Replace <MEDIA_LENGTH> with the media length.  
  MediaObject mediaInfo = MediaHeartbeat.createMediaObject(  
      <MEDIA_NAME>,  
      <MEDIA_ID>,  
      <MEDIA_LENGTH>,  
      MediaHeartbeat.StreamType.VOD
  );

  // Set to true if this is a resume playback scenario
  mediaInfo.setValue(MediaHeartbeat.MediaObjectKey.mediaResumed, true);

  _heartbeat.trackSessionStart(mediaInfo, mediaMetadata);
}
```

### iOS

```
- (void)onMainmediaLoaded:(NSNotification *)notification {
  //Replace <MEDIA_NAME> with the media name.
  //Replace <MEDIA_ID> with a media unique identifier.
  //Replace <MEDIA_LENGTH> with the media length.     
  ADBMediaObject *mediaObject =  
    [ADBMediaHeartbeat createMediaObjectWithName:<MEDIA_NAME>
                       mediaId:<MEDIA_ID>
                       length:<MEDIA_LENGTH>
                       streamType:ADBMediaHeartbeatStreamTypeVOD];

  //Set to YES if this user is resuming a previously closed media session
  [mediaObject setValue:@(YES) forKey:ADBMediaObjectKeymediaResumed];

  [_mediaHeartbeat trackSessionStart:mediaObject data:mediaMetadata];
}

```

### JavaScript

```js
_onmediaLoad = function () {
  // Replace <MEDIA_NAME> with the media name.
  // Replace <MEDIA_ID> with a media unique identifier.
  // Replace <MEDIA_LENGTH> with the media length.  
  var mediaObject =  
    MediaHeartbeat.createMediaObject(<MEDIA_NAME>,  
                                     <MEDIA_ID,  
                                     <MEDIA_LENGTH>,  
                                     MediaHeartbeat.StreamType.VOD);

  // Set to true if this user is resuming a previously closed media session
  mediaObject.setValue(MediaObjectKey.mediaResumed, true);
  this._mediaHeartbeat.trackSessionStart(mediaObject, contextData);
};
```
