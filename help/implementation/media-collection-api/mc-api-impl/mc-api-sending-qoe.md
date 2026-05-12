---
title: Sending QoE Data
description: Learn about sending events with a qoeData JSON key.
uuid: 52a02d92-195d-4ce8-8ce3-585ed68969f9
exl-id: 41a20410-78e6-481d-bd5c-0febadb290d8
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/gLf-vtHwf0I5JVPyfUj2479exPaAXYu2gyYUU2V5Glw
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
# Sending QoE data{#sending-qoe-data}

Every event can be decorated with an extra JSON key called `qoeData`, which is positioned alongside the `params` key in the JSON request body.

>[!NOTE]
>
>You should check the [JSON validation schemas](mc-api-validate-reqs.md) to verify parameter types and whether they are mandatory or optional.
