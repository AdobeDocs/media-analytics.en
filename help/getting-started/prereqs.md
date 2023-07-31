---
title: Learn About Prerequisites for Streaming Media
description: Get Started with Adobe Analytics Streaming Media. Learn what you need to implement Adobe Analytics for Streaming Media.
uuid: 4c0b37f3-8615-4cc0-b9c9-eeb029067064
exl-id: 85ab1dbd-f4a7-4f11-afc9-8d5000e2de70
feature: "Media Analytics, System Requirements"
role: User, Admin, Data Engineer
---
# Prerequisites {#prerequisites}

Before you begin implementing Streaming Media, complete the following tasks:

1. **Review the Streaming Media overview**<br>
Before you begin implementing Streaming Media, review the [Streaming Media overview](/help/media-overview.md) to make sure Streaming Media meets your needs.

1. **Confirm your Steaming Media pricing model**<br>
The current pricing model is based on video streams. If necessary, contact your Sales Representative or Adobe Account Team, as Streaming Media is sold separately, as an add-on to Adobe Analytics.<!--update when media SKUs are added to other AEP apps -->

1. **Enable Adobe Analytics Reports**<br>
To enable reports in Analytics and to view the content and ad data that you're collecting, you must enable reports in Analytics. See [Media reports enablement](/help/reporting/media-reports-enable.md).

1. **Implement the Adobe Experience Platform Identity Service in Experience Cloud**
   
   The **Identity Service** enables the common identification framework for the Experience Cloud Core Services, solutions, and customer attributes and audiences in the People core service. It works by assigning a unique, persistent ID to a site visitor. When your organization implements the ID service, this ID lets you identify the same site visitor and their data in different Experience Cloud solutions.

   ![ID Service graphic](assets/mc_id_service_graphic.png)

   The ID service can also replace the different solution-specific IDs (for example, Analytics AID). Through the [Customer IDs and Authentication States](https://experienceleague.adobe.com/docs/id-service/using/reference/authenticated-state.html) functionality, the ID service lets you pass in your own customer IDs to the Experience Cloud. Keep in mind, however, that the ID service only works with the solutions to which you have already subscribed. If you are not signed up for access to other products, the ID service does not provide the access.

   The ID service is an integral component of many Experience Cloud features, enhancements, and services. Currently, the ID service supports [Analytics,](https://www.adobe.com/marketing-cloud/web-analytics.html) [Audience Manager,](https://www.adobe.com/marketing-cloud/data-management-platform.html) and [Target.](https://www.adobe.com/marketing-cloud/testing-targeting.html)

   If you have not implemented the ID service, now is the time to start considering a migration strategy. For more information about the importance and role of the ID service, see [Why the Identity Service Should be on Your Radar.](https://theblog.adobe.com/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)

   For additional information about the Experience Cloud ID, see [Experience Cloud ID Overview,](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html) and [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html).

1. **View additional prerequisites for your implementation method** 
   
      Depending on how you plan to implement Streaming Media, view the prerequisites for either of the following implementation methods:
 
      * [Prerequisites for Adobe Analytics-only implementations](/help/implementation/media-sdk/setup/prerequisites-analytics.md)
   
      * [Prerequisites for Edge implementations](/help/implementation/edge/prerequisites-edge.md)

      Use the [Implementation overview](/help/implementation/overview.md) to determine which implementation method is right for you.
