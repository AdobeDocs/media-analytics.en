---
title: What is Adobe Audience Manager enablement?
description: Learn how to link application actions to media tracking data without the need for additional processing rules and custom variables.
exl-id: c0d73bc2-4713-498a-8882-ff66c7f3dd50
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/oInE3GwgI1k5-UbqMUm9yvjXfIF0SsRXPrnUWmWT9Ww
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
  - id: e7d92df1-c5ba-4e93-85df-f83171b889be
    internal-label: Variables
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
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
---
# Audience Manager enablement{#audience-manager-enablement}

Adobe Audience Manager (AAM), a Data Management Platform (DMP), helps you bring your audience data assets together, making it easy to collect commercially relevant information about site visitors, create marketable segments, and serve targeted advertising and content to the right audience.

With AAM, you are not tied to a data seller, exchange, or demand-side platform. Additionally, AAM is completely agnostic when it comes to your partners’ data assets. With access to multiple data sources, AAM offers digital publishers the ability to use a wide variety of third-party data. To learn more about AAM, see the AAM documentation [Audience Manager Product Documentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/aam-home.html).

**VA to AAM data transfer -** For both video content and video ads, the metrics and metadata that are collected by using solution (reserved) variables can be automatically sent to AAM. The data transfer is available across all platforms including desktop, mobile, and OTT. To enable this server-side data transfer, you need to reach out to Adobe Client Care and ask for this feed to be enabled.

>[!IMPORTANT]
>
>To ensure the smooth transfer of data to AAM, you should be on the latest versions of the Media SDK libraries.

Federated Data fully supports data sharing to AAM. Please work with your Adobe team for confirmation of Federated Data settings.

## OTT / AAM methods {#ott-aam-methods}

You can use these methods to send signals and retrieve visitor segments from Audience Manager:

### Chromecast {#am-chromecast}

* `getVisitorProfile() -`

   Returns the visitor profile that was most recently obtained. Returns an empty object if no signal has been submitted yet.

   ```js    
   ADBMobile.audienceManager.getVisitorProfile();
   ```

* `getDpid() -`

   Returns the visitor profile that was most recently obtained. Returns an empty object if no signal has been submitted yet.

   ```js    
   ADBMobile.audienceManager.getDpid();
   ```

* `getDpuuid() -`

   Returns the current DPUUID.

   ```js    
   ADBMobile.audienceManager.getDpuuid();
   ```

* `setDpidAndDpuuid() -`

   Sets the DPID and DPUUID. If DPID and DPUUID are set, they will be sent with each signal.

   ```js    
   ADBMobile.audienceManager.setDpidAndDpuuid("myDpid", "myDpuuid");
   ```

* `submitSignal() -`

   Sends audience management a signal with traits.

   ```js
   ADBMobile.audienceManager.submitSignal({"sampleTrait":"sampleValue"});
   ```

### Roku {#am-roku}

* `audienceVisitorProfile -`

   Returns the visitor profile that was most recently obtained. Returns an empty object if no signal has been submitted yet.

   ```js    
   ADBMobile().audienceVisitorProfile()
   ```

* `audienceDpid -`

   Returns the visitor profile that was most recently obtained. Returns an empty obje t if no signal has been submitted yet.

   ```js    
   ADBMobile().audienceDpid()
   ```

* `audienceDpuuid -`

   Returns the current DPUUID.

   ```js    
   ADBMobile().audienceDpuuid()
   ```

* `audienceSetDpidAndDpuuid -`

   Sets the DPID and DPUUID. If DPID and DPUUID are set, they will be sent with each signal.

   ```js    
   ADBMobile().audienceSetDpidAndDpuuid("myDpid", "myDpuuid")
   ```

* `audienceSubmitSignal -`

   Sends audience management a signal with traits.

   ```js    
   traitData = {}
   traitData["sampleTrait"] = "sampleValue"
   ADBMobile().audienceSubmitSignal(traitData)
   ```
