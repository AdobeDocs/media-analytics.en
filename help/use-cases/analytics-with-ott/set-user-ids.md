---
title: Set User IDs
description: APIs for setting user IDs, which server as a unique customer identifier.
uuid: fdd54fec-79cd-4bf8-b17e-4d61d84f6310
exl-id: 6b451082-47f3-4e65-9fe0-cecb2d20dc2d
feature: Streaming Media, API
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/AG7KGMEVhpDbGzHKhb94KF8QHzDTw-y1kdkklOdWCFI
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
# Set user IDs{#set-user-ids}

The user ID is a unique custom visitor identifier defined by the application for a user.

Set and get the unique user ID on the ADBMobile SDK as follows:

* **Set:**

   * **Roku:**

      ```    
      ADBMobile().setUserIdentifer("app-generated-unique-id")
      ```

   * **Chromecast:**

      ```    
      ADBMobile().config.setUserIdentifer("app-generated-unique-id");
      ```

* **Get:**

   * **Roku:**

      ```    
      vid = ADBMobile().userIdentifer()
      ```

   * **Chromecast:**

      ```    
      vid = ADBMobile().config.getUserIdentifer();
      ```
