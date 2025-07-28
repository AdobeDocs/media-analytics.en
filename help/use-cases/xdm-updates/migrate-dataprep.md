---
title: Migrate DataPrep for custom fields to the new Streaming Media fields
description: Learn how to migrate data type DataPrep for custom fields to the new Streaming Media fields
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Migrate DataPrep for custom fields to the new Streaming Media fields

This document describes the process of migrating the DataPrep service that exists on top of Adobe Data Collection flows enabled for Adobe Analytics for Streaming Media data. The migration should convert a DataPrep mapping from a previous "media.mediaTimed" to a custom field path to a current mapping of "mediaReporting" equivalent to the same custom field path.
Migration guidelines
To migrate the DataPrep mappings from the old field called "Media" to the new field called "Media Reporting Details" we will need to edit the DataPrep mappings.
In Adobe Experience Platform (AEP), under the Sources section, navigate to the Dataflows tab to locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Analytics. Once identified, use the Update dataflow option to modify the DataPrep setup by replacing every custom source mapping that contains a deprecated field with the new corresponding field from the new XDM object.
The migration steps will be the following:
*
Ensure you have been notified that ADC was deployed using the new mediaReporting fields, the following steps must be executed only after the release in order to not lose any data;
*
Locate mappings containing source fields from the deprecated "Media" object;
*
Replace those sources by using fields from the new "Media Reporting Details" object;
*
Validate that the mappings are still working as expected.
Mapping between the old fields and the new fields can be found here. More precisely, the old field path can be found under the "XDM Field Path" property while the new field path can be found under the "Reporting XDM Field Path".
Hands-On example
Let's take an example to make it easier to follow the migration guidelines.
On our example dataflow we have a single mapping, so in this case we will need to apply the migration guidelines only once.
Adobe Confidential - Shared under NDA
First, we will need to enter the editing UI. In Adobe Experience Platform (AEP), under the Sources section, navigate to the Dataflows tab to locate the dataflow responsible for importing Streaming Media data from Adobe Analytics to Adobe Experience Platform via Adobe Analytics. Once identified, use the Update dataflow to enter the editing UI as shown in the below image.

![AEP dataflow](assets/aep-dataflow.jpeg)

Once we are in the Mapping tab select Custom, identify the custom mappings that rely on media.mediaTimed fields as sources.

![AEP dataflow continued](assets/aep-dataflow2.jpeg)

In this example, the target field is under "_dcbl" because we created a custom fieldgroup on the schema in our development organization. The custom fieldgroup path differs based on the organization name.
For each mapping that uses the media.mediaTimed object, find its correspondent in the mediaReporting object using this documentation. As an example, for Network, the correspondent for media.mediaTimed.primaryAssetViewDetails.broadcastNetwork is mediaReporting.sessionDetails.network.

![Updated XDM field path](assets/xdm-field-path-old-and-new.jpeg)

In the source field replace media.mediaTimed path with the mediaReporting path while the target field remains unchanged.

![AEP dataflow continued](assets/aep-dataflow3.jpeg)

Finally, click on the next button to save your change.
There will be some time when the status will be in Processing mode. When status is back in Enabled changes will have been applied.

![AEP dataflow continued](assets/aep-dataflow5.jpeg)

In the above example we had all involved data types as String so the mapping replacement was direct.
In case you have the source field data type different than the target field data type, you need to follow guidelines in troubleshooting guide, handling data formats and mapping functions from DataPrep.
Examples:
If the source type is a string and the target type is a boolean, Data Prep can automatically parse the value and convert the source value to a boolean. (Handling data formats)

If the source type is a number and the target type is a boolean, you need to use data manipulation functions:
Mapping with media.mediaTimed to a custom field.

![AEP dataflow continued](assets/aep-dataflow6.jpeg)

Mapping with mediaReporting to the same custom field:

![AEP dataflow continued](assets/aep-dataflow7.jpeg)


