---
title: Opt-out and Privacy Explained
description: Learn how to handle opt-in, opt-out, and privacy.
uuid: 7e60c7bd-8dba-4c7a-9c3c-0c634b815397
exl-id: 64f5ef2b-7850-43d8-8f32-3d008ea4f156
feature: Streaming Media
role: User, Admin, Developer
---
# Opt-out and privacy{#opt-out-and-privacy}

## Opt-out / Opt-in {#opt-out-opt-in}

You can control whether tracking activity is allowed on a specific device:

* **Mobile Apps -** The VA library respects the `AdobeMobile` library's privacy and opt-out settings. To opt-out of tracking, you need to use the `AdobeMobile` library. For more information on the `AdobeMobile` library's opt-out and privacy settings, see [Opt-Out and Privacy Settings](https://experienceleague.adobe.com/docs/mobile-services/android/gdpr-privacy-android/privacy.html).
* **JavaScript/Browser Apps -** The VA library respects the `VisitorAPI` privacy and opt­out settings. To opt­out of tracking, you need to opt out from the Visitor API service. For further information on opt­out and privacy, see [Adobe Experience Platform Identity Service.](https://experienceleague.adobe.com/docs/id-service/using/home.html).
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

## Analytics opt-out parameters {#analytics-opt-out}

Two reserved parameters let you suppress Media Analytics data from server-side forwarding to Audience Manager and from data sharing with third parties. These are passed alongside session parameters at the API level, not set on the SDK config object.

| Parameter | API key | Context data |
| --- | --- | --- |
| Opt out of server-side forwarding | `analytics.optOutServerSideForwarding` | `cm.dmp` |
| Opt out of data sharing | `analytics.optOutSellToThirdParty` | `cm.sell` |

* **`analytics.optOutServerSideForwarding`**: when `true`, suppresses server-side forwarding of this hit to Audience Manager and other Adobe destinations.
* **`analytics.optOutSellToThirdParty`**: when `true`, suppresses sharing of this hit data with third-party partners.

>[!NOTE]
>
>These parameters are documented in the [Media Collection API sessions reference](/help/implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md). They apply to Media Collection API and Media Edge API implementations. The SDK-level opt-out controls described above apply to Mobile and OTT implementations.
