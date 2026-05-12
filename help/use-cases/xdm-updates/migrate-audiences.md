---
title: Migrate audiences to the new Adobe Analytics for Streaming Media data type
description: Learn how to migrate audiences to the new Adobe Analytics for Streaming Media data type
feature: Streaming Media
role: User, Admin, Developer
exl-id: 5664bf56-b228-430a-944c-faaab55fa108
TQID: https://experienceleague.adobe.com/TqsfcR2JgxVjDNx3-CBBa9n6pwvuGk9JgQ--DvWeHg0
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
---
# Migrate audiences to the new streaming media fields

This document describes how an audience that uses fields from the Adobe streaming media services data type called "Media" should be migrated to use the new corresponding data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)."

## Migrate an audience

To migrate an audience from the old data type called "Media" to the new data type called "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)," you must edit the audience and in each rule replace the old field from the deprecated data type with the new corresponding field from the new data type:

1. Locate rules containing fields from the deprecated "Media" data type. This is all fields that begin with the path, `media.mediaTimed`.

1. Duplicate those rules using fields from the new "[Media Reporting Details](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/media-reporting-details)" data type.

1. Keep both rules in place until you validate that the audiences are working as expected.

1. Remove the rules that contain fields from the deprecated "Media" data type.

1. Validate that the audiences are still working as expected.

See the [Content ID](/help/reporting/dimensions/content.md) parameter and the rest of the streaming media variables documented under [Streaming media services](/help/media-overview.md) to map between the old fields and the new fields. The old field path is found under the "XDM Field Path" property while the new field path is found under the "Reporting XDM Field Path" property.

![Old and new XDM field paths](assets/field-paths-updated.jpeg)

## Example

To make it easier to follow the migration guidelines, consider the following example that contains an audience with a single rule. Because the audience has a single rule, you need to apply the migration guidelines only once.

1. Select the [!UICONTROL **Edit audience**] button in the upper-right corner.

1. Locate the rules configured for the audience.

   ![Edit audience](assets/audience-edit.jpeg)

   ![Edit audience](assets/audience-edit2.jpeg)

1. Select the rule to open its configuration.

   ![Edit audience](assets/audience-edit3.jpeg)

1. (Optional) To view the path of the field used in the rule, select the info button near the field name.

   ![Edit audience](assets/audience-edit4.jpeg)

1. Identify the field name (in this case "Media Starts"). 

   ![Edit audience](assets/audience-edit5.jpeg)

1. See the streaming media variables documented under [Streaming media services](/help/media-overview.md) to map between the old fields. The old field path can be found under the "XDM Field Path" property while the new field path can be found under the "Reporting XDM Field Path" property. As an example, for the [Media Starts](/help/reporting/metrics/media-starts.md) parameter, the correspondent for `media.mediaTimed.impressions.value` is `mediaReporting.sessionDetails.isViewed`.

   ![Updated XDM path](assets/updated-xdm-path.jpeg)

1. Add the same rule as the existing one using the new field.

   ![Add rule](assets/add-rule.jpeg)

   ![Add rule](assets/add-rule2.jpeg)

   ![Add rule](assets/add-rule3.jpeg)

1. Select [!UICONTROL **Save**] to save the audience. You can keep this setup for as long as you need to validate that the audience is still working as expected.

1. After the validation is complete, remove the old field, then select [!UICONTROL **Save**] to save the audience.

   ![Add rule](assets/add-rule4.jpeg)

1. Validate the audience again.

   The audience migration process is complete.
