---
seo-title: Track app actions
title: Track app actions
uuid: 9cdc048a-419a-4725-bd61-6ca6d909cf10
index: y
internal: n
snippet: y
---

# Track app actions{#track-app-actions}

Actions are the events that occur in your app that you want to measure.

Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might send a `trackAction` call for each new subscription, each time a content is rated, or each time a level is completed. Actions are not tracked automatically, so call `trackAction` when an event that you want to track occurs, and map the action to a custom event.

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

