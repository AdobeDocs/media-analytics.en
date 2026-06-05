---
title: Learn About Prerequisites for Adobe streaming media services
description: Get Started with the streaming media services. Learn what you need for implementation.
uuid: 4c0b37f3-8615-4cc0-b9c9-eeb029067064
exl-id: 85ab1dbd-f4a7-4f11-afc9-8d5000e2de70
feature: Streaming Media, Workspace Basics
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/e9iYwDwT-zSSZ3hV20U1w7p-MtKaK4Q8-vGMCrnenpc
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
    internal-label: Reports
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: c8add8f2-4250-4fd9-9cde-9707036c567d
    internal-label: Methods
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
# Prerequisites {#prerequisites}

Before you begin implementing Adobe streaming media services, complete the following tasks:

1. **Confirm your pricing model**<br>
The current pricing model for the Customer Journey Analytics Streaming Media Collection Add-on and the Adobe Analytics for Streaming Media Add-on is based on video streams. If necessary, contact your Sales Representative or Adobe Account Team, as the add-on is sold separately for Adobe Analytics and Adobe Experience Platform.

1. **Enable Adobe Analytics Reports** *(Analytics-only implementations)*<br>
To enable reports in Analytics and to view the content and ad data that you're collecting, you must enable reports. See [Set up reporting for Analytics-only implementations](/help/reporting/setup/analytics-reporting.md).

1. **Configure identity**<br>

   Identity configuration requirements differ depending on your implementation method:

   * **Edge implementations**: Identity is handled through the Adobe Experience Platform Identity namespace configuration. No separate Identity Service setup is required. See [Edge implementation overview](/help/implementation/edge/overview.md) for details.

   * **Analytics-only implementations**: The Adobe Experience Platform Identity Service must be enabled to identify visitors consistently across CX Enterprise solutions. The Identity Service assigns a unique, persistent ID to each site visitor and allows that ID to be shared across all CX Enterprise solutions you subscribe to.

     For more information, see the [Adobe Experience Platform Identity Service documentation](https://experienceleague.adobe.com/docs/id-service/using/home.html).

1. **View additional prerequisites for your implementation method**

      Depending on how you plan to implement streaming media services, view the prerequisites for either of the following implementation methods:

      * [Analytics-only implementation overview](/help/implementation/analytics-only/overview.md)

      * [Edge implementation overview](/help/implementation/edge/overview.md)

      Use the [Implementation overview](/help/implementation/overview.md) to determine which implementation method is right for you.
