---
title: Migrate profiles to the new Streaming Media fields
description: Learn how to migrate profiles to the new Streaming Media fields
feature: Streaming Media
role: User, Admin, Developer
exl-id: 0f75e594-5216-4ac1-91bd-fa89ab4b2110
TQID: https://experienceleague.adobe.com/c1WHnEeZnI3PP6aO40pDHpJCi2Z0ERiNY8lCj4wyMiU
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
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Migrate profiles to the new streaming media fields

This document describes the process of migrating the profile filtering service that exists on top of the Adobe Data Collection flows that are enabled for Adobe Analytics for streaming media data. The migration converts the profile filtering service from using the Adobe streaming media services data type called "Media" to use the new corresponding data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)."

## Migrate profiles

To migrate the profile filtering from the old data type called "Media" to the new data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)," you must edit the existing profile filtering rules:

1. In Adobe Experience Platform, under the [!UICONTROL **Sources**] section, go to the [!UICONTROL **Dataflows**] tab.

1. Locate the dataflow responsible for importing streaming media data from Adobe Analytics to Adobe Experience Platform via Adobe Data Collection.

1. Select [!UICONTROL **Update dataflow**] to modify the profile filtering setup by replacing every custom rule that contains a deprecated field with the new corresponding field from the new XDM object.

1. Locate the filters containing fields from the deprecated "Media" object.

1. Append those filters by adding fields from the new "Media Reporting Details" object.

1. Use an OR operator between the two fields;

1. Validate that the profiles are still working as expected.

See the [Content ID](/help/reporting/dimensions/content.md) parameter and the rest of the streaming media variables documented under [Streaming media services](/help/media-overview.md) to map between the old fields and the new fields. The old field path can be found under the "XDM Field Path" property while the new field path can be found under the "Reporting XDM Field Path" property.

## Example

To make it easier to follow the migration guidelines, consider the following example dataflow that contains a single profile filtering rule. In this case, since there is only a single rule, you need to apply the migration guidelines only once.

1. In Adobe Experience Platform, under the [!UICONTROL **Sources**] section, go to the [!UICONTROL **Dataflows**] tab.

1.Locate the dataflow responsible for importing streaming media data from Adobe Analytics to Adobe Experience Platform via Adobe Analytics. 

1. Select **[!UICONTROL Update dataflow]** to enter the editing UI as shown in the below image.

   ![AEP dataflow profile](assets/aep-dataflow-profile.jpeg)

1. Select **[!UICONTROL Next]** to go to the Filtering tab.

   ![AEP dataflow filter tab](assets/aep-dataflow-filtering-profile.jpeg)

1. On the **[!UICONTROL Filtering]** tab, identify the filtering rules that rely on `media.mediaTimed` fields.

   ![AEP dataflow filter rules](assets/dataflow-filtering-rules-profile.jpeg)


   For each filter that uses the meda.mediaTimed object, find its correspondent in the `mediaReporting` object using the streaming media variables documented under [Streaming media services](/help/media-overview.md) to map between the old fields and the new fields. The old field path is found under the "XDM Field Path" property while the new field path is found under the "Reporting XDM Field Path" property. As an example, for [Media Starts](/help/reporting/metrics/media-starts.md), the correspondent for `media.mediaTimed.impressions.value` is `xdm.mediaReporting.sessionDetails.isViewed`.

   ![New and old XDM fields](assets/xdm-fields-new-and-old.jpeg)

1. Drag the relevant `mediaReporting` field to the filtering rule and use the OR operator between the two rules. Add the same rule as the existing one when using the new field.

   ![Add filter rules](assets/add-filter-rules.jpeg)

1. Select **[!UICONTROL Next]** to save your changes.
