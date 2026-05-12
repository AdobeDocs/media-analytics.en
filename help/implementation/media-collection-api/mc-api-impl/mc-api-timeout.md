---
title: Timeout Conditions
description: Learn about the Media Collection  API timeout conditions.
uuid: 2a4ea13e-a561-4adf-b567-f980301b32c8
exl-id: 0b494b27-a4a6-4af7-84c1-c44b33b6da8f
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/13vwFrp3NF-e-odFn3eXIuhHusl14ovkwhTpPYbJC0U
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
# Timeout conditions{#timeout-conditions}

**Media Collection API Timeout Conditions** 

The Media Collection API, being stateless, does not have the same mechanism as the Media SDK for issuing a new Session ID when timeout conditions occur. When a timeout condition occurs, the back end will close the session, and all subsequent calls made with that Session ID will be dropped. The logic that handles a Session Timeout must be handled in the client. That is, the player will have to monitor the timeout conditions, and obtain a new Session ID if a timeout occurs.

* **10 Minutes: No API Events** 

   If the back end does not receive any API events it will close the session.
* **30 Minutes: No Playhead Change** 

   If the playhead does not move for 30 minutes (e.g., the user hits Pause and walks away), the back end will close the session.

>[!NOTE]
>
>You can also force a session end by sending an `events` request with the `sessionEnd` event type.
