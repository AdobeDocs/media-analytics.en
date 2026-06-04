---
title: Migrate Data Prep for custom fields to the new Streaming Media fields
description: Learn how to migrate the data type Data Prep for custom fields to the new Streaming Media fields
feature: Streaming Media
role: User, Admin, Developer
exl-id: 7294b147-2bef-463f-bada-cb67c16d01b0
TQID: https://experienceleague.adobe.com/57wAwVCwAUlRcMAbFW-X6T6Fe7Ap6leOaQw2Vx9r3OA
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
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Migrate Data Prep for custom fields to the new streaming media fields

This document describes the process of migrating the Data Prep service that exists on top of the Adobe Data Collection flows that are enabled for Adobe Streaming Media Collection data. The migration converts a Data Prep mapping from the Adobe Streaming Media Collection data type called "Media" to use the new corresponding data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)."

## Migrate Data Prep for custom fields

To migrate the Data Prep mappings from the old data type called "Media" to the new data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)," you must edit the Data Prep mappings:

>[!IMPORTANT]
>
>To avoid losing data, ensure that the Analytics source connector has been deployed using the new `mediaReporting` fields before completing the steps in this section. 

1. In Adobe Experience Platform, under the **[!UICONTROL Sources]** section, go to the **[!UICONTROL Dataflows]** tab.

1. Locate the dataflow responsible for importing streaming media data from Adobe Analytics to Adobe Experience Platform via Adobe Data Collection. 

1. Select **[!UICONTROL Update dataflow]** to modify the Data Prep setup by replacing every custom source mapping that contains a deprecated field with the new corresponding field from the new XDM object.

1. Locate the mappings containing source fields from the deprecated "Media" object.

1. Replace those sources by using fields from the new "Media Reporting Details" object.

1. Validate that the mappings are still working as expected.

See the [Content ID](/help/reporting/dimensions/content.md) parameter and the rest of the streaming media variables documented under [Streaming media services](/help/media-overview.md) to map between the old fields and the new fields. The old field path is found under the "XDM Field Path" property while the new field path is found under the "Reporting XDM Field Path" property.

## Example

To make it easier to follow the migration guidelines, consider the following example dataflow that contains a single mapping. In this case, you need to apply the migration guidelines only once.

1. In Adobe Experience Platform, under the **[!UICONTROL Sources]** section, go to the **[!UICONTROL Dataflows]** tab. 

1. Locate the dataflow responsible for importing streaming media data from Adobe Analytics to Adobe Experience Platform via Adobe Data Collection. 

1. Select **[!UICONTROL Update dataflow]** to enter the editing UI as shown in the below image.

   ![AEP dataflow](../../assets/aep-dataflow.jpeg)

1. In the **[!UICONTROL Mapping]** tab, select **[!UICONTROL Custom]**.

1. Identify the custom mappings that rely on `media.mediaTimed` fields as sources.

   ![AEP dataflow continued](../../assets/aep-dataflow2.jpeg)

   In this example, because you created a custom field group on the schema in your development organization, the target field is under `_dcbl`. The custom field group path differs based on the organization name.

1. For each mapping that uses the `media.mediaTimed` object, find its correspondent in the `mediaReporting` object using this documentation. 

   As an example, for Network, the correspondent for `media.mediaTimed.primaryAssetViewDetails`.broadcastNetwork is `xdm.mediaReporting.sessionDetails.network`.

   ![Updated XDM field path](../../assets/xdm-field-path-old-and-new.jpeg)

1. In the **[!UICONTROL Source field]** field, replace the `media.mediaTimed` path with the `mediaReporting` path. The target field remains unchanged.

   ![AEP dataflow continued](../../assets/aep-dataflow3.jpeg)

1. Select **[!UICONTROL Next]** to save your changes.

   The status shows as **[!UICONTROL Processing]**. After the changes are applied, the status shows as **[!UICONTROL Enabled]**. 

   ![AEP dataflow continued](../../assets/aep-dataflow5.jpeg)

## Example with different data types

In the above example, all of the data types involved were String, so the mapping replacement was direct.

If the source field data type is different than the target field data type, you need to follow the guidelines in the [Data Prep troubleshooting guide](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/troubleshooting-guide), [Handling data formats with Data Prep](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling), and [Data Prep mapping functions](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling).

For example, if the source type is a string and the target type is a boolean, Data Prep can automatically parse the value and convert the source value to a boolean. 

If the source type is a number and the target type is a boolean, you need to use data manipulation functions:

Mapping with `media.mediaTimed` to a custom field.

![AEP dataflow continued](../../assets/aep-dataflow6.jpeg)

Mapping with `mediaReporting` to the same custom field:

![AEP dataflow continued](../../assets/aep-dataflow7.jpeg)
