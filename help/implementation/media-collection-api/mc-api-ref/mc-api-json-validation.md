---
title: Streaming Media Services JSON Validation Schemas
description: What are Steaming Media JSON validation schemas and how are they used to determine the correct request body parameters for each type of event.
uuid: 7c9d5ce4-f5d2-4129-900e-4d02800907d1
exl-id: 2931715d-2e7d-4c15-8569-da63b43d6006
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/ZWKv1LJKc8qLkZYpcNdDFEs8Er70toRCoufarMcgVKQ
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
# JSON validation schemas{#json-validation-schemas}

The Streaming Media Collection back-end validates the request parameters for each event type using JSON validation schemas. These schemas are available to you, and serve as the current authority on parameter types used in the MA API.

`GET https://{uri}/api/v1/schemas/{event-type}`

For more information about using the JSON validation schemas, see [Validating event requests.](../mc-api-impl/mc-api-validate-reqs.md)
