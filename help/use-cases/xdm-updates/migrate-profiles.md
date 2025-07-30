---
title: Migrate profiles to the new Streaming Media fields
description: Learn how to migrate profiles to the new Streaming Media fields
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Migrate profiles to the new Streaming Media fields

This document describes the process of migrating the profile filtering service that exists on top of the Adobe Data Collection flows that are enabled for Adobe Analytics for Streaming Media data. The migration converts the profile filtering service from using the Adobe Streaming Media Collection data type called "Media" to use the new corresponding data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)."

## Migrate profiles

To migrate the profile filtering from the old data type called "Media" to the new data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)," you must edit the existing profile filtering rules:

1. In Adobe Experience Platform, under the [!UICONTROL **Sources**] section, go to the [!UICONTROL **Dataflows**] tab.

1. Locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Data Collection.

1. Select [!UICONTROL **Update dataflow**] to modify the profile filtering setup by replacing every custom rule that contains a deprecated field with the new corresponding field from the new XDM object.

1. Locate the filters containing fields from the deprecated "Media" object.

1. Append those filters by adding fields from the new "Media Reporting Details" object.

1. Use an OR operator between the two fields;

1. Validate that the profiles are still working as expected.

See the [Content ID](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters#content-id) parameter on the [Audio and video parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters) page to map between the old fields and the new fields. The old field path can be found under the "XDM Field Path" property while the new field path can be found under the "Reporting XDM Field Path" property.

## Example

To make it easier to follow the migration guidelines, consider the following example dataflow that contains a single profile filtering rule. In this case, since there is only a single rule, you need to apply the migration guidelines only once.

1. In Adobe Experience Platform, under the [!UICONTROL **Sources**] section, go to the [!UICONTROL **Dataflows**] tab.

1.Locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Analytics. 

1. Select **[!UICONTROL Update dataflow]** to enter the editing UI as shown in the below image.

   ![AEP dataflow profile](assets/aep-dataflow-profile.jpeg)

1. Select **[!UICONTROL Next]** to go to the Filtering tab.

   ![AEP dataflow filter tab](assets/aep-dataflow-filtering-profile.jpeg)

1. On the **[!UICONTROL Filtering]** tab, identify the filtering rules that rely on media.mediaTimed fields.

   ![AEP dataflow filter rules](assets/dataflow-filtering-rules-profile.jpeg)


   For each filter that uses the meda.mediaTimed object, find its correspondent in the mediaReporting object using the [Audio and video parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters) page to map between the old fields and the new fields. The old field path is found under the "XDM Field Path" property while the new field path is found under the "Reporting XDM Field Path" property. As an example, for [Media Starts](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters#media-starts), the correspondent for media.mediaTimed.impressions.value is mediaReporting.sessionDetails.isViewed.

   ![New and old XDM fields](assets/xdm-fields-new-and-old.jpeg)

1. Drag the relevant mediaReporting field to the filtering rule and use the OR operator between the two rules. Add the same rule as the existing one when using the new field.

   ![Add filter rules](assets/add-filter-rules.jpeg)

1. Select **[!UICONTROL Next]** to save your changes.
