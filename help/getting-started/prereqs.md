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

1. **Review the Adobe streaming media services overview**<br>
Before you begin implementing streaming media services, review the [Adobe streaming media services overview](/help/media-overview.md) to make sure it meets your needs.

1. **Confirm your pricing model**<br>
The current pricing model for the Customer Journey Analytics Streaming Media Collection Add-on and the Adobe Analytics for Streaming Media Add-on is based on video streams. If necessary, contact your Sales Representative or Adobe Account Team, as the add-on is sold separately for Adobe Analytics and Adobe Experience Platform.

1. **Enable Adobe Analytics Reports**<br>
To enable reports in Analytics or Customer Journey Analytics and to view the content and ad data that you're collecting, you must enable reports. See [Media reports enablement](/help/implementation/media-sdk/setup/media-reports-enable.md).

1. **Implement the Adobe Experience Platform Identity Service in CX Enterprise**
   
   The **Identity Service** enables the common identification framework for CX Enterprise Core Services, solutions, and customer attributes and audiences in the People core service. It works by assigning a unique, persistent ID to a site visitor. When your organization implements the ID service, this ID lets you identify the same site visitor and their data in different CX Enterprise solutions.

   ![ID Service graphic](assets/mc_id_service_graphic.png)

   The ID service can also replace the different solution-specific IDs (for example, Analytics AID). Through the [Customer IDs and Authentication States](https://experienceleague.adobe.com/docs/id-service/using/reference/authenticated-state.html) functionality, the ID service lets you pass in your own customer IDs to CX Enterprise. Keep in mind, however, that the ID service only works with the solutions to which you have already subscribed. If you are not signed up for access to other products, the ID service does not provide the access.

   The ID service is an integral component of many CX Enterprise features, enhancements, and services. Currently, the ID service supports [Analytics,](https://www.adobe.com/marketing-cloud/web-analytics.html) [Audience Manager,](https://www.adobe.com/marketing-cloud/data-management-platform.html) and [Target.](https://www.adobe.com/marketing-cloud/testing-targeting.html)

   If you have not implemented the ID service, now is the time to start considering a migration strategy. For more information about the importance and role of the ID service, see [Why the Identity Service Should be on Your Radar.](https://theblog.adobe.com/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)

   For additional information about the Experience Cloud ID, see [Experience Cloud ID Overview,](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html) and [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html).

1. **View additional prerequisites for your implementation method** 
   
      Depending on how you plan to implement streaming media services, view the prerequisites for either of the following implementation methods:
 
      * [Prerequisites for Adobe Analytics-only implementations](/help/implementation/media-sdk/setup/prerequisites-analytics.md)
   
      * [Prerequisites for Edge implementations](/help/implementation/edge/prerequisites-edge.md)

      Use the [Implementation overview](/help/implementation/overview.md) to determine which implementation method is right for you.
