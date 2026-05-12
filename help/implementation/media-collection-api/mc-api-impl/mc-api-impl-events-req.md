---
title: Implementing an Events Request
description: Learn how to use the Events request endpoint for all subsequent tracking calls after you obtain a Session ID
uuid: 3bfa313c-ff74-4e2e-bbde-6f4a6221d85b
exl-id: af9a3470-85c7-498e-9bf4-6df3c6aafad9
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/xJntEcDm5sCGoCeuCjl9x51EOaYcOO2FzFAtK8mbt38
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
# Implementing an events request{#implementing-an-events-request}

**`{uri}/api/v1/sessions/{sid}/events`**

Use the [Events request](../mc-api-ref/mc-api-events-req.md) for all subsequent tracking calls after you obtain a Session ID using the [Sessions request.](../mc-api-ref/mc-api-sessions-req.md) Specify the playhead location and timestamp, the event type, and any optional parameters you want to include, in the JSON body of the request.

The JSON request body for the [Events request](../mc-api-ref/mc-api-events-req.md) has the same structure as that of the Sessions request, however check the [JSON validation schemas](../mc-api-ref/mc-api-json-validation.md) for parameter requirements and types.
