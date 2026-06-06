---
title: Opt-out and privacy settings
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
# Opt-out and privacy settings

When a user opts out of tracking, the streaming media library immediately stops all data collection activity. No session start calls, no heartbeat pings, and no event tracking data is sent to Adobe data collection servers for that user.

## Opt-out / Opt-in

Opt-out controls operate per device or browser. Respecting user consent is the responsibility of the implementing organization. For an overview of Adobe's privacy practices, see the [Adobe Privacy Center](https://www.adobe.com/privacy.html).

## Recommended implementation types

>[!BEGINTABS]

>[!TAB Web SDK]

The Web SDK respects the consent preferences set using the `setConsent` command. When consent is set to `"out"`, the Web SDK stops forwarding all events, including streaming media tracking calls, to the Edge Network. Consent state persists in browser storage between sessions.

Before implementing opt-out, ensure that your Web SDK is configured with the Streaming Media component. For more information, see [Set up Web SDK](../implementation/edge/web-sdk.md).

Set consent to opted out using the Adobe 2.0 consent standard:

```javascript
alloy("setConsent", {
  consent: [{
    standard: "Adobe",
    version: "2.0",
    value: {
      collect: { val: "n" }
    }
  }]
});
```

Consent values:

* `"y"`: Opted in (data collection allowed)
* `"n"`: Opted out (data collection suppressed)
* `"p"`: Pending (awaiting user decision; no data collected until resolved)

To restore tracking, call `setConsent` again with `"y"` as the `collect.val` value.

See the [setConsent command](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/setconsent) in the Web SDK documentation for other formats, including IAB TCF 2.0.

>[!TAB iOS]

The Adobe Experience Platform Mobile SDK respects the privacy status set using `MobileCore.setPrivacyStatus()`. Setting the status to `.optedOut` suppresses all data collection across all AEP extensions, including Streaming Media. The status persists across app sessions.

```swift
MobileCore.setPrivacyStatus(.optedOut)
```

To restore tracking, set the privacy status back to `.optedIn`:

```swift
MobileCore.setPrivacyStatus(.optedIn)
```

For more information, see [Privacy and GDPR](https://developer.adobe.com/client-sdks/resources/privacy-and-gdpr/#setprivacystatus) in the AEP Mobile SDK documentation.

>[!TAB Android]

The Adobe Experience Platform Mobile SDK respects the privacy status set using `MobileCore.setPrivacyStatus()`. Setting the status to `MobilePrivacyStatus.OPT_OUT` suppresses all data collection across all AEP extensions, including Streaming Media. The status persists across app sessions.

```kotlin
MobileCore.setPrivacyStatus(MobilePrivacyStatus.OPT_OUT)
```

To restore tracking, set the privacy status back to `MobilePrivacyStatus.OPT_IN`:

```kotlin
MobileCore.setPrivacyStatus(MobilePrivacyStatus.OPT_IN)
```

For more information, see [Privacy and GDPR](https://developer.adobe.com/client-sdks/resources/privacy-and-gdpr/#setprivacystatus) in the AEP Mobile SDK documentation.

>[!TAB Roku]

The AEP Roku SDK uses `setConsent()` with the Adobe 2.0 consent standard. Setting `collect.val` to `"n"` immediately stops all data collection, including streaming media events.

Consent values:

* `"y"` — Opted in (data collection allowed)
* `"n"` — Opted out (data collection suppressed)
* `"p"` — Pending (awaiting user decision; no data collected until resolved)

```brightscript
currentDate = CreateObject("roDateTime")
timestampInISO8601 = currentDate.ToISOString("milliseconds")

collectConsentNo = {
  "consent": [{
    "standard": "Adobe",
    "version": "2.0",
    "value": {
      "metadata": { "time": timestampInISO8601 },
      "collect": { "val": "n" }
    }
  }]
}

m.aepSdk.setConsent(collectConsentNo)
```

To restore tracking, set `collect.val` to `"y"` and call `setConsent()` again.

You can also set a default consent value at SDK initialization using `updateConfiguration()` with the `ADB_CONSTANTS.CONFIGURATION.CONSENT_DEFAULT` key. For more information, see the [AEP Roku SDK documentation](https://github.com/adobe/aepsdk-roku).

>[!TAB Media Edge API]

The Media Edge API is a server-side implementation. No SDK layer automatically enforces consent — your application must check user consent status before making any API calls and suppress requests for opted-out users.

For full opt-out, do not POST to the `/va/v2/sessions` endpoint (or any subsequent event endpoints) for users who have opted out:

```javascript
// Check consent status before initiating a media session
if (userHasOptedOut) {
  // Do not call the Media Edge API
  return;
}

// Only call the API for users who have not opted out
fetch("https://edge.adobedc.net/va/v2/sessions", {
  method: "POST",
  body: JSON.stringify(sessionStartPayload)
});
```

For more information, see the [Media Edge API reference](https://developer.adobe.com/data-collection-apis/docs/endpoints/media/).

>[!ENDTABS]

## Legacy implementation types (Analytics-only)

>[!BEGINTABS]

>[!TAB Media SDK JS 3.x]

The Media SDK JS 3.x library defers to the Adobe Visitor API (Identity Service) opt-out state. When a user opts out using the Visitor API, the Media SDK automatically suppresses all tracking calls.

```javascript
var visitor = Visitor.getInstance("YOUR_ORG_ID@AdobeOrg");
visitor.setOptOut(true);
```

Replace `YOUR_ORG_ID@AdobeOrg` with your organization ID from Adobe Admin Console.

To restore tracking, pass `false` to `setOptOut()`.

For more information, see [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html).

>[!TAB Chromecast]

The Chromecast Media SDK 3.x respects the privacy status set using `ADBMobile.config.setPrivacyStatus()`. Setting the status to `PRIVACY_STATUS_OPT_OUT` suppresses all data collection.

```javascript
ADBMobile.config.setPrivacyStatus(ADBMobile.config.PRIVACY_STATUS_OPT_OUT);
```

To restore tracking, set the status back to opted in:

```javascript
ADBMobile.config.setPrivacyStatus(ADBMobile.config.PRIVACY_STATUS_OPT_IN);
```

You can also set the default privacy status at SDK initialization in your `ADBMobileConfig` object:

```javascript
var ADBMobileConfig = {
  "analytics": {
    "privacyDefault": "optedout"
  }
};
```

>[!TAB Media Collection API]

The Media Collection API is a server-side implementation. Your application must check user consent status before making API calls and suppress requests for opted-out users.

For full opt-out, do not POST to the sessions endpoint for users who have opted out.

For partial opt-outs under CCPA, include opt-out flags in the `params` object of your `sessionStart` request:

```json
{
  "playerTime": { "playhead": 0, "ts": 1699523820000 },
  "eventType": "sessionStart",
  "params": {
    "analytics.optOutServerSideForwarding": true,
    "analytics.optOutShare": true
  }
}
```

* `analytics.optOutServerSideForwarding`: Set to `true` to opt out of data being shared between Adobe Analytics and other Experience Cloud solutions (such as Audience Manager).
* `analytics.optOutShare`: Set to `true` to opt out of federated data sharing with other Adobe Analytics clients.

For a full list of available parameters, see the [Media Collection API request parameters reference](../implementation/media-collection-api/mc-api-ref/mc-api-req-params.md).

>[!ENDTABS]
