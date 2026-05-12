---
title: Setting the HTTP Request Type in Your Player
description: The request body for all Media Collection API requests must be in JSON format. Learn how to set the content request type in your player.
uuid: b8fa7233-e654-4acf-a9d7-14158cded13e
exl-id: 9ab3eb07-8f0d-4f9a-8feb-db20c4de3db4
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/Zrsv5Kjec6ZHzcOEcj5Ek0zXdwM8cF7HFalKs-MKGQU
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
# Setting the HTTP request type {#setting-the-http-request-type}

The request body for all Media Collection API requests must be in JSON format, so you should set the content request type in your player. For example, in JavaScript you would set the `Content-Type` request header as follows: 

```
httpRequest.setRequestHeader('Content-Type', 'application/json'); 
```
