---
title: Handling Application Interrupts During Playback
description: Learn how to handle interruptions to tracking during playback of media.
uuid: 1ccb4507-bda6-462d-bf67-e22978a4db3d
exl-id: a84af6ad-dd4f-4f0d-93dd-66f2f84ddc0e
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/BlL-c1rf5d3juDKHybex9vrPvQsBIiNXVO2ug9LKl0g
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
# Handling application interrupts during playback{#handling-application-interrupts-during-playback}

Playback in a media application can be interrupted in a variety of ways. For example, a user can explicitly press pause, or a user can put the application into the background. Regardless of what causes an interruption in media playback, the tracking instructions are the same.

1. Call **`trackPause`** when the application is interrupted (goes to background, media pauses, etc.).
1. Call **`trackPlay`** when the application returns to the foreground and/or the media resumes playing.

>[!NOTE]
>
>Calling `trackSessionStart` when the app returns from the background can result in the playback up to that point not counting towards the total playback time, along with losing earlier progress markers, segments, and so on. Instead, call `trackPlay` when the app returns and/or the media resumes playing.

## FAQ about handling application interrupts: {#faq-about-handling-application-interrupts}

* _How long should an app be backgrounded before the session closes?_

   If the application allows background playback, it can continue tracking by calling our APIs and we will send all our regular tracking pings. Not many video apps allow background playback except for YouTube Red, however, all audio apps allow this. If the application does not allow background playback, then it is advisable to stay in the Pause State for one minute, and then end the tracking session. The application cannot continue sending Pause pings, because in most cases it cannot determine if the user is going to return to continue viewing the media, or determine when it is going to be killed. It is also a bad experience to keep sending pings when in the background.

* _What is the correct way to handle re-starting tracking after the app has been in the background for a long time?_

   The application should call `trackSessionEnd` to end the tracking session. From Version 2.1, the SDK sends an "end" ping to notify the back-end that the tracking session is closed.

* _What about restarting the same session?_

   For information about resuming a tracking session, see [Resuming inactive sessions](resuming-inactive.md).The SDK sends a resume ping to notify the back-end that the user is manually resuming the session.
