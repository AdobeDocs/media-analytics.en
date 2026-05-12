---
title: Sending Ping Events
description: Ping events are the heartbeat of Adobe streaming media services. Learn how to send a timed ping for main content or and ad tracking.
uuid: c92c1a92-3af6-4474-9e42-ffb8f6c94b33
exl-id: 0a645363-26d5-41e7-aa16-c775253e2b1d
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/EJ6R7DILB56bcHgAki-Lvto3yYbuhf-wYfklvPElDeM
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
