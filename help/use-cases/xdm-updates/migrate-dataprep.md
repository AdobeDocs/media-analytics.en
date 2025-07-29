---
title: Migrate DataPrep for custom fields to the new Streaming Media fields
description: Learn how to migrate data type DataPrep for custom fields to the new Streaming Media fields
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Migrate DataPrep for custom fields to the new Streaming Media fields

This document describes the process of migrating the DataPrep service that exists on top of Adobe Data Collection flows enabled for Adobe Analytics for Streaming Media data. The migration should convert a DataPrep mapping from a previous "media.mediaTimed" to a custom field path to a current mapping of "mediaReporting" equivalent to the same custom field path.

## Migrate DataPrep for custom fields

To migrate the DataPrep mappings from the old data type called "Media" to the new data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)," you must edit the DataPrep mappings:

>[!IMPORTANT]
>
>To avoid losing data, ensure that the Analytics Source Connector has been deployed using the new mediaReporting fields before completing the steps in this section. 

1. In Adobe Experience Platform, under the [!UICONTROL **Sources**] section, go to the [!UICONTROL **Dataflows**] tab, then locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Analytics. 

1. Select [!UICONTROL **Update dataflow**] to modify the DataPrep setup by replacing every custom source mapping that contains a deprecated field with the new corresponding field from the new XDM object.

1. Locate the mappings containing source fields from the deprecated "Media" object.

1. Replace those sources by using fields from the new "Media Reporting Details" object.

1. Validate that the mappings are still working as expected.

See the [Content ID](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters#content-id) parameter on the [Audio and video parameters](https://experienceleague.adobe.com/en/docs/media-analytics/using/implementation/variables/audio-video-parameters) page to map between the old fields and the new fields. The old field path can be found under the "XDM Field Path" property while the new field path can be found under the "Reporting XDM Field Path" property.

## Example

To make it easier to follow the migration guidelines, consider the following example dataflow that contains a single mapping. In this case, we will need to apply the migration guidelines only once.

1. In Adobe Experience Platform, under the **[!UICONTROL Sources]** section, go to the **[!UICONTROL Dataflows]** tab to locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Analytics. 

1. Select **[!UICONTROL Update dataflow]** to enter the editing UI as shown in the below image.

   ![AEP dataflow](assets/aep-dataflow.jpeg)

1. In the **[!UICONTROL Mapping]** tab, select **[!UICONTROL Custom]**.

1. Identify the custom mappings that rely on media.mediaTimed fields as sources.

   ![AEP dataflow continued](assets/aep-dataflow2.jpeg)

   In this example, the target field is under "_dcbl" because we created a custom fieldgroup on the schema in our development organization. The custom fieldgroup path differs based on the organization name.

1. For each mapping that uses the media.mediaTimed object, find its correspondent in the mediaReporting object using this documentation. 

   As an example, for Network, the correspondent for media.mediaTimed.primaryAssetViewDetails.broadcastNetwork is mediaReporting.sessionDetails.network.

   ![Updated XDM field path](assets/xdm-field-path-old-and-new.jpeg)

1. In the **[!UICONTROL Source field]** field replace media.mediaTimed path with the mediaReporting path while the target field remains unchanged.

   ![AEP dataflow continued](assets/aep-dataflow3.jpeg)

1. Select the **[!UICONTROL Next]** button to save your change.

   The status shows as **[!UICONTROL Processing]**. After the changes are applied, the status shows as **[!UICONTROL Enabled]**. 

   ![AEP dataflow continued](assets/aep-dataflow5.jpeg)

## Example with different data types

In the above example, all of the data types involved were String, so the mapping replacement was direct.

If the source field data type is different than the target field data type, you need to follow guidelines in the [Data Prep troubleshooting guide](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/troubleshooting-guide), [Handling data formats with Data Prep](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling) and [Data Prep mapping functions](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling).

For example, if the source type is a string and the target type is a boolean, Data Prep can automatically parse the value and convert the source value to a boolean. (Handling data formats)

If the source type is a number and the target type is a boolean, you need to use data manipulation functions:
Mapping with media.mediaTimed to a custom field.

![AEP dataflow continued](assets/aep-dataflow6.jpeg)

Mapping with mediaReporting to the same custom field:

![AEP dataflow continued](assets/aep-dataflow7.jpeg)


