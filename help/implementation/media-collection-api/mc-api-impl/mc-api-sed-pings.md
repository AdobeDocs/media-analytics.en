---
title: Sending Ping Events
description: Ping events are the heartbeat of Adobe streaming media services. Learn how to send a timed ping for main content or and ad tracking.
uuid: c92c1a92-3af6-4474-9e42-ffb8f6c94b33
exl-id: 0a645363-26d5-41e7-aa16-c775253e2b1d
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Sending ping events{#sending-ping-events}

**You must fire ping events every 10 seconds, beginning after 10 seconds of playback, regardless of other API events that you have sent. This applies for both main content and ad tracking.** 

The ping events are the "heartbeat" of the Adobe streaming media services. The only required parameters for a ping call are `eventType: ping` along with the `playerTime` object (playhead position and timestamp). 

The following code snippet shows one way to implement a timed pinging mechanism for main content (10 second interval): 

```js
... 
Pinger.init(10000); 
... 
Pinger.kill();

var Pinger = { 
    init: function(interval) { 
        this._timer = window.setInterval(function() { 
                $.event.trigger({type: "onPing", _data: ""}); 
            }, interval); 
    }, 
     
    kill: function() { 
        window.clearInterval(this._timer); 
    } 
}
```
