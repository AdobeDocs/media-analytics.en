---
title: Learn How to Implement Standard Ad Metadata on iOS
description: How to use standard ad metadata in ad tracking on iOS.
uuid: f15fb727-5a5b-46c5-bf12-93b376c10fd1
exl-id: 018ae833-51d9-4ff0-80e7-3dbcaefb997c
feature: Streaming Media
role: User, Admin, Developer
TQID: https://experienceleague.adobe.com/a02N5s2UCX1r6eRbaO-8e8djvDA-r9jhWFcELICBY8E
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: bcc784b7-4ade-4c84-96fa-2f7631b1e5fd
    internal-label: Media Analytics
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
---
# Implement standard ad metadata on iOS{#implement-standard-ad-metadata-on-ios}

## Ad constants

|  Constant name  | Description&nbsp;&nbsp;  |
|---|---|
|  `ADBMediaObjectKeyStandardAdMetadata`  | Constant for attaching standard ad metadata on `AdInfo ADBMediaObject`  |

## Implement standard ad metadata

For standard ad metadata, create a dictionary of standard ad metadata key value pairs using the keys for your platform: 

```
// Sample implementation for using standard metadata keys for Ad 
NSMutableDictionary *standardAdMetadata = [[NSMutableDictionary alloc] init]; 
[standardAdMetadata setObject:@"Sample Advertiser" forKey:ADBAdMetadataKeyADVERTISER]; 
[standardAdMetadata setObject:@"Sample Campaign" forKey:ADBAdMetadataKeyCAMPAIGN_ID]; 
 
[adObject setValue:standardAdMetadata forKey:ADBMediaObjectKeyStandardAdMetadata];
```

[iOS metadata keys](/help/use-cases/track-av-playback/impl-std-metadata/ios-metadata-keys.md)
