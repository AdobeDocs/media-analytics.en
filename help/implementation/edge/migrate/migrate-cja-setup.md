---
title: Migrate audiences to the new Adobe Analytics for Streaming Media data type
description: Learn how to migrate audiences to the new Adobe Analytics for Streaming Media data type
feature: Streaming Media
role: User, Admin, Developer
exl-id: 67e67a4b-bd61-4247-93b7-261bd348d29b
TQID: https://experienceleague.adobe.com/Y-Y-xWKm-zOzaQm8kMbgGx8r6BTNLl-Q5AltlF5v7aA
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
feature_v2:
  - id: b3f03848-ae12-48b2-8aab-cad18567eb32
    internal-label: Metrics
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
---
# Migrate Customer Journey Analytics to use the new streaming media fields

This document describes how a Customer Journey Analytics setup that uses the Adobe streaming media services data type called "Media" should be updated to use the new corresponding data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)."

## Migrate Customer Journey Analytics 

To migrate a Customer Journey Analytics setup from the old data type called "Media" to the new data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)," you must update the following setups that are using the old data type:

* Data views

* Derived fields

### Migrate data views

To migrate the data views to the new data type:

1. Locate all the data views using the deprecated "Media" data type. This is all fields for which the path begins with `media.mediaTimed`.

1. Do either of the following:

   * In those data views, insert the fields from the new "Media Reporting Details" data type. 

   * Create a derived field that uses the new "Media Reporting Details" data type if it is set, or that falls back to the old "Media" data type if the "Media Reporting Details" data type is not set.

### Migrate derived fields

To migrate derived fields to the new data type:

1. Locate all the derived fields using the deprecated "Media" data type. This is all derived fields that contain fields for which the path begins with `media.mediaTimed`.

1. Replace all the old fields in the derived field with the new corresponding field from "Media Reporting Details."

See the [Content ID](/help/reporting/dimensions/content.md) parameter and the rest of the streaming media variables documented under [Streaming media services](/help/media-overview.md) to map between the old fields and the new fields. The old field path is found under the "XDM Field Path" property while the new field path is found under the "Reporting XDM Field Path" property.

![Old and new XDM field paths](assets/field-paths-updated.jpeg)

## Example

To make it easier to follow the migration guidelines, consider the following example that contains a data view with fields from the old deprecated "Media" data type. In this data view, you need to add the new corresponding fields. 

### Update the data view

You can use either of the following options to update the data view:

#### Option 1

1. Locate a metric or a dimension that is using the old field from the deprecated data type.

   ![Old field path in data view](assets/old-field-data-view.jpeg)

1. Check the corresponding new field in the [Chapter offset](/help/reporting/dimensions/chapter-offset.md) article.

1. Locate the new corresponding field in the data view.

   ![New field path in data view](assets/new-field-data-view.jpeg)

1. Drag the new field to the metric or dimension.

1. Repeat this process for all metrics and dimensions that use fields from the deprecated "Media" data type.

#### Option 2

This option creates a derived field that selects the value from the old field or the value from the new field based on which one exists for a specific event. This derived field replaces the old "Media" data type in any projects where it is being used.

If you want to create a derived field for the "Chapter Name" that uses the new "Media Reporting Details" data type if it is set, or that falls back to the old "Media" data type if the "Media Reporting Details" data type is not set:

1. Drag a "Case When" clause into the derived fields.

   ![Customize the new field to create a data view](assets/create-derived-field2.jpeg)

1. Populate the **[!UICONTROL If]** clause using the value of the **Reporting XDM Field Path**, as shown on the [Chapter name](/help/reporting/dimensions/chapter-name.md) page.

   ![Chapter name](assets/chapter-name.jpeg)

   ![Chapter name](assets/chapter-name2.jpeg)

   ![Derived field condition](assets/derived-field-condition.jpeg)

   ![Derived field chapter name](assets/derived-field-chapter-name.jpeg)

1. Populate the fallback value using the old field from the deprecated "Media" data type.

   ![Fallback value](assets/fallback-value.jpeg)

   ![Fallback value](assets/fallback-value2.jpeg)

   This is the final definition of the derived field.

   ![Derived field complete](assets/derived-field-complete.jpeg)

1. To update the derived fields, locate a derived field that is using the old deprecated fields (path starting with `media.mediaTimed`).

   ![derived field](assets/old-derived-field.jpeg)

1. Mouse over the derived field that you want to update, then select the **[!UICONTROL Edit]** icon.

1. Locate all the fields from the old data type (path starting with `media.mediaTimed`) and replace them with the new corresponding field.

   ![Locate field with old data type](assets/locate-fields-with-old-datatype.jpeg)

1. Check the corresponding new field in the [Content Name](/help/reporting/dimensions/content-name.md) article.

1. Replace the old field with the new field.

   ![New field](assets/derived-field-new.jpeg)

1. Repeat this process for all the derived fields using fields from the old deprecated "Media" data type.

   The migration of the CJA setup is completed.
