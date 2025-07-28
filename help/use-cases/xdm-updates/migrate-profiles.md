---
title: Migrate profiles to the new Streaming Media fields
description: Learn how to migrate profiles to the new Streaming Media fields
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Migrate profiles to the new Streaming Media fields

This document describes the process of migrating the profile filtering service that existing on top of Adobe Data Collection flows enabled for Adobe Analytics for Streaming Media data. The migration should convert the profile filtering service from using the deprecated "media.mediaTimed" XDM path to using the new "mediaReporting" field.
Migration guidelines
To migrate the profile filtering from the old field called "Media" to the new field called "Media Reporting Details" we will need to edit the existing profile filtering rules.
In Adobe Experience Platform (AEP), under the Sources section, navigate to the Dataflows tab to locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Data Collection. Once identified, use the Update dataflow option to modify the profile filtering setup by replacing every rule that contains a deprecated field with the new corresponding field from the new XDM object.
The migration steps will be the following:
*
Locate filters containing fields from the deprecated "Media" object;
*
Append those filters by adding fields from the new "Media Reporting Details" object;
*
Use an OR operator between the two fields;
*
Validate that the profiles are still working as expected.
Mapping between the old fields and the new fields can be found here. More precisely, the old field path can be found under the "XDM Field Path" property while the new field path can be found under the "Reporting XDM Field Path".
Hands-On example
Let's take an example to make it easier to follow the migration guidelines.
On our example dataflow we have a single profile filtering rule, so in this case since we have a single rule, we will need to apply the migration guidelines only once.
First, we will need to enter the editing UI. In Adobe Experience Platform (AEP), under the Sources section, navigate to the Dataflows tab to locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Data Collection. Once identified, use the Update dataflow to enter the editing UI as shown in the below image.

![AEP dataflow profile](assets/aep-dataflow-profile.jpeg)

Select Next to go to the Filtering tab.

![AEP dataflow filter tab](assets/aep-dataflow-filtering-profile.jpeg)

Once we are in the Filtering tab, identify the filtering rules that rely on media.mediaTimed fields.

![AEP dataflow filter rules](assets/dataflow-filtering-rules-profile.jpeg)

For each filter that uses the meda.mediaTimed object, find its correspondent in the mediaReporting object using this documentation. As an example, for Media Starts, the correspondent for media.mediaTimed.impressions.value is mediaReporting.sessionDetails.isViewed.

![New and old XDM fields](assets/xdm-fields-new-and-old.jpeg)

Drag and drop the relevant mediaReporting field to the filtering rule and use the OR operator between the two rules. Add the exact same rule as the existing one when using the new field.

![Add filter rules](assets/add-filter-rules.jpeg)

Finally, click on the next button to save your change.
