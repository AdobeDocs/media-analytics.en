---
title: Track App Actions
description: App actions are the events that occur in your app that you want to measure.
uuid: 9cdc048a-419a-4725-bd61-6ca6d909cf10
exl-id: 88b7d540-67b7-4ec1-8273-02e34853bf60
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/ahqWp2yjs-zkd9dTRWTkE7b6KE-WpwVR0OH9vCqTPjI
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: f1f1a2d4-0976-4881-b091-c2bb8de7ffac
    internal-label: Events
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# Track app actions{#track-app-actions}

Actions are the events that occur in your app that you want to measure.

Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might send a `trackAction` call for each new subscription, or each time content is rated, or each time a level is completed. 

Actions are not tracked automatically, so call `trackAction` when an event that you want to track occurs, and map the action to a custom event.

1. When an event that you want to track occurs, call `trackAction`.

   * **Roku:**

     ```js    
     ADBMobile().trackAction("myapp.ActionName", {})
     ```    

   * **Chromecast:**

     ```js    
     ADBMobile.analytics.trackAction("myapp.ActionName", {});
     ```

1. Map the action to a custom event.

   * **Roku:**

     ```js    
     dictionary = {} 
     dictionary["myapp.social.SocialSource"] = "Twitter"  
     ADBMobile().trackAction("myapp.SocialShare", dictionary)
     ```    

   * **Chromecast:**

     ```js    
     var dictionary = {}; 
     dictionary["myapp.social.SocialSource"] = "Twitter"; 
     ADBMobile.analytics.trackAction("myapp.SocialShare", dictionary);
     ```

You can also send additional context data with each track action call.
