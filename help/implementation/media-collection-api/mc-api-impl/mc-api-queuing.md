---
title: Queueing Events When Sessions Response is Slow
description: Learn what to do when the Session ID is returned after your player fires events.
uuid: 39ea59d9-89d3-4087-a806-48a43ecf0c98
exl-id: 2c23c378-c104-4256-b6e7-8eb6871f62da
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/maOCcXZJkPef7edi3UtaSIJKa-4x9byaH6Qzt2eDR2Y
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
---
# Queueing events when sessions response is slow{#queueing-events-when-sessions-response-is-slow}

The Media Collection API is RESTful: i.e, you make an HTTP request and wait for the response. This is an important point only for when you make a [Sessions request](../mc-api-ref/mc-api-sessions-req.md) to obtain a Session ID at the beginning of video playback. This is important because the Session ID is required for all subsequent tracking calls.

It is possible that your player may fire events _before the Sessions response returns_ (with the Session ID parameter) from the backend. If this occurs, your app must queue any tracking events that arrive between the [Sessions request](../mc-api-ref/mc-api-sessions-req.md) and its response. When the Sessions response arrives, you should first process any queued [events](../mc-api-ref/mc-api-events-req.md), then you can start processing _live_ events with the [Events](../mc-api-ref/mc-api-events-req.md) calls.

>[!NOTE]
>
>The [Events request](../mc-api-ref/mc-api-events-req.md) does not return data back to the client beyond an HTTP response code.

Check the Reference Player in your distribution for one way to process events prior to receiving a Session ID. For example:

```js
var eventData = {};            // JSON payload 
eventData.playerTime = getPlayerTime(); // Required 
eventData.eventType = "play";           // Required 
eventData.params = {};                  // Optional for events 
 
VideoPlayer.prototype._collectEvent =  
  function(eventData) { 
 
    // If we don't have a Session ID yet,  
    // queue the event and return... 
    if (!sessionStarted) { 
        console.log("[Player] Queueing event "); 
        _pendingEvents.push(eventData); 
        return; 
    } 
 
    // If we DO have a Session ID, process the 
    // tracking event...     
    apiClient.request({ 
        "baseUrl": "{endpoint}", 
        "path": "api/v1/{sid}/events", // events request 
        "method": "POST", 
        "data": eventData 
    }).then((response) => {   
        […] 
    } 
} 
 
VideoPlayer.prototype.collectEvent =  
  function (eventType, eventParams) { 
         
    if (typeof eventParams === 'undefined') {   
        eventParams = {}; 
    } 
 
    this._collectEvent({                   
        eventType: eventType,            // Required 
        playerTime: getPlayerTime(),     // Required 
        params: eventParams              // Optional  
    });                                    
}; 
 
VideoPlayer.prototype.getPlayerTime = function() { 
    return { 
        playhead: this.getPlayhead(),    // playhead value in seconds 
        ts: this.getCurrentTimestamp()   // timestamp value in milliseconds 
    }; 
};
```

**Process any queued events -** The reference player processes queued events as follows: 

```js
    […] 
    this._processPendingEvents();    // Once you have a Session ID, 
    […]                              // process any queued events 
 
VideoPlayer.prototype._processPendingEvents =  
  function() { 
    this._pendingEvents.forEach((eventData) => { 
        this._collectEvent(eventData); 
    }); 
 
    this._pendingEvents = []; 
}
```

Continue to process tracking events as they occur.
