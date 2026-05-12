---
title: Track App States
description: App states are the different screens or views in your application. Learn how to track the app state in your application using the trackState call.
uuid: 2f98fb43-c362-4a9b-8732-fa7e963da729
exl-id: bb1e0eee-7c59-40b4-9359-a7441b9686b8
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/fVNQ4CIqXbSYyi32rBlB2B9S6YTsBwxJhD3XaeDcDIE
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
---
# Track app states{#track-app-states}

States are the different screens or views in your application. Each time a new state is displayed in your application, you should send a `trackState` call. For example, when a user navigates from the home page to the video details screen, send a `trackState` call. States are typically viewed by using a pathing report, so you can see how users navigate your app and which states are most commonly viewed. 

## trackState calls

You typically call `trackState` each time the app loads a new screen.

### Roku

```js
ADBMobile().trackState("State Name", {})
```

### Chromecast

```js
ADBMobile.analytics.trackState("State Name",{});
```

The state name is reported in the "View State" variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In other Analytics interfaces, "View State" is reported as "Page Name"; "State Views" is reported as "Page Views".

## Send context data

In addition to "State Name", you can send additional context data with each track state call.

### Roku

```js
dictionary = { } 
dictionary["myapp.login.LoginStatus"] = "logged in"  
ADBMobile().trackState("Home Screen", dictionary)
```

### Chromecast

```js
var dictionary = { }; 
dictionary["myapp.login.LoginStatus"] = "logged in"; 
ADBMobile.analytics.trackState("Home Screen", dictionary); 
```

>[!NOTE]
>
>Context data values must be mapped to custom variables in Adobe Mobile services.
