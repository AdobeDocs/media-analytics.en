---
title: Opt-out and Privacy explained
description: Learn how to handle opt-in, opt-out, and privacy.
uuid: 7e60c7bd-8dba-4c7a-9c3c-0c634b815397
exl-id: 64f5ef2b-7850-43d8-8f32-3d008ea4f156
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/eF09wxu2mIUoFph5EdHz5y0XtcpXHHLINqSGLQEMoHU
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
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Opt-out and privacy{#opt-out-and-privacy}

## Opt-out / Opt-in {#opt-out-opt-in}

You can control whether tracking activity is allowed on a specific device:

* **Mobile Apps -** The Media Extensions respects the privacy settings in Data Collection. To opt out of tracking, you need to set up privacy to [Opted out in Tags](https://developer.adobe.com/client-sdks/documentation/getting-started/create-a-mobile-property/#create-a-mobile-property) or [Update privacy status in Mobile SDK](https://developer.adobe.com/client-sdks/resources/privacy-and-gdpr/#getprivacystatus).
* **JavaScript/Browser Apps -** The VA library respects the `VisitorAPI` privacy and opt­out settings. To opt­out of tracking, you need to opt out from the Visitor API service. For further information on opt­out and privacy, see [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html).
* **OTT Apps (Chromecast, Roku) -** The OTT SDKs provide General Data Protection Regulation (GDPR)-ready APIs that allow you to set `opt` status flags for data collection and transmission, and to retrieve locally stored identities.

  >[!NOTE]
  >
  >Media heartbeat tracking calls are also disabled if the privacy status is set to opt-out.

  You can control whether or not Analytics data is sent on a specific device using the following settings:

    * The `privacyDefault` setting in the `ADBMobile.json` config file. This controls the initial setting and persists until it is changed in code.

    * The `ADBMobile().setPrivacyStatus()` method.

        * **Opt out:**

            * **Chromecast:**

              ```            
              ADBMobile.config.setPrivacyStatus(ADBMobile.config.PRIVACY_STATUS_OPT_OUT)
              ```

            * **Roku:**

              ```            
              ADBMobile().setPrivacyStatus(ADBMobile().PRIVACY_STATUS_OPT_OUT)
              ```

          >[!IMPORTANT]
          >
          >When a user opts out of tracking, all of the persisted device data and IDs will be purged until the user opts back in.

        * **Opt back in:**

            * **Chromecast:**

              ```            
              ADBMobile.config.setPrivacyStatus(ADBMobile.config.PRIVACY_STATUS_OPT_IN)
              ```

            * **Roku:**

              ```            
              ADBMobile().setPrivacyStatus(ADBMobile().PRIVACY_STATUS_OPT_IN)
              ```

        * **Return the current setting:**

            * **Chromecast:**

              ```            
              ADBMobile.config.getPrivacyStatus()
              ```

            * **Roku:**

              ```            
              ADBMobile().getPrivacyStatus()
              ```

  After the privacy setting is changed using `setPrivacyStatus`, the change is permanent until it is changed again using this method, or the app is uninstalled and reinstalled.

## Retrieving Stored Identifiers (OTT Apps) {#retrieving-stored-identifiers-ott-apps}

This information helps you retrieve locally stored user identities from your Roku app.

>[!IMPORTANT]
>
>The method for retrieving all identifiers gets all user identities known and persisted by the SDK. You must call this method **before** a user opts-out.

The locally stored identities are returned in a JSON string, which might contain:

* Company Context - IMS Org IDs
* User IDs
* Experience Cloud ID (MCID)
* Data Source IDs (DPID, DPUUID)
* Analytics IDs (AVID, AID, VID, and associated RSIDs)
* Audience Manager ID (UUID)

For example:

* **Chromecast:**

  ```
  ADBMobile.config.getAllIdentifiersAsync(callback)
  ```

* **Roku:**

  ```
  vids = ADBMobile().getAllIdentifiers()
  ```
