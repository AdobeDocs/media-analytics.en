---
title: Updated XDM fields for collecting Streaming Media data into Adobe Experience Platform
description: Learn about updated XDM fields for collecting Streaming Media data into Adobe Experience Platform
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Migrate to the updated XDM fields for collecting Streaming Media data into Adobe Experience Platform

>[!NOTE]
>
>This information is intended for organizations who are using the Adobe Source Connector to bring Streaming Media data from Adobe Analytics into Adobe Experience Platform for use with Customer Journey Analytics reporting or any other Platform service. 
>
>The changes do not impact Adobe Analytics as a stand-alone application, including data collection, processing, and reporting. Tools such as Data Feeds and Processing Rules remain unaffected, so no updates to the Analytics implementation are required.

A new Adobe Data Collection (Analytics Source Connector) implementation for the Streaming Media service is now available that migrates from one set of XDM fields to another. 

## New XDM field path

As part of this migration, the `mediaReporting` XDM field path was added to the XDM schemas used in Adobe Data Collection (Analytics Source Connector) flows. Any existing and newly generated Adobe Data Collection schema will automatically include this new field.

## Replacement of the old XDM field path

All Adobe Data Collection (Analytics Source Connector) flows that transfer Streaming Media data from Adobe Analytics to Adobe Experience Platform are currently sending data both on the new `mediaReporting` XDM field path and the old `media.mediaTimed` XDM field path. Both of these field paths will be available for three months, through the end of October 2025. After October, the `media.mediaTimed` fields will be fully deprecated, and data ingested after October will include only `mediaReporting`. After deprecation, the `media.mediaTimed` fields will no longer be visible in the Adobe Experience Platform schema UI, and data ingestion on these fields will stop. Consequently, these fields will no longer be available for use in any Adobe Experience Platform service. 

Data that was ingested before this date will remain available for reporting proposes. 

## Additional differences with the new XDM field path

With the new Adobe Source Connector implementation for Streaming Media, keep-alive calls from Adobe Analytics are now ingested into Adobe Experience Platform. 

Previously, these calls were not reflected in Platform apps such as Customer Journey Analytics. As a result, your organization might observe the following differences in reporting:

* **Accurate session counts**: In some cases, this might mean deflation in session counts, because keep-alive calls help maintain active user sessions even in the absence of direct media interactions. These keep-alive calls are generated every 20 minutes after the last event, per media playback, with the intent to keep the visit open. To ensure optimal session tracking in Customer Journey Analytics, it is recommended to configure the visit expiration to 30 minutes in the Data View.

* **An increase in the number of events**: Because keep-alive calls are now counted in the Customer Journey Analytics Events metric. If you want to exclude keep-alive calls from reporting, you can create a filter that excludes events that have Event Type of `media.keepalive`.

This change ensures greater alignment between Analytics and CJA reporting.

## Migrate your existing setup

To ensure a smooth transition, all customers must migrate existing setups from `media.mediaTimed` fields to `mediaReporting` fields before the end of October 2025. The affected areas are those that rely on `media.mediaTimed` usage, and they should be migrated as outlined in the following sections.

### Customer Journey Analytics** 

There are two ways in which CJA reports can be migrated:

>[!NOTE]
>
>After choosing one of the following options, you must manually replace each `media.mediaTimed` field used in Customer Journey Analytics reports with its corresponding Derived Field or Reporting XDM Field Path.

* **To retain historical data**: Adobe teams have developed a predefined Customer Journey Analytics template that introduces a set of derived fields that combine the old and new XDM fields into a single field. This template can be enabled per data view upon request. Please contact our support team to further assist you in enabling the new fields. Note: These derived fields will not count toward your organization's derived field limit and will be added on top of it.

* **If historical data is not required**: It is sufficient to use the Reporting XDM Field Path at reporting time. For more information, see [Migrate Customer Journey Analytics to use the new Streaming Media fields](/help/use-cases/xdm-updates/migrate-cja-setup.md).

### Real-Time CDP

All Audiences and Profiles must be based on `mediaReporting`. For more information, see [Migrate profiles to the new Streaming Media fields](/help/use-cases/xdm-updates/migrate-profiles.md).

### Data Stream / Data Collection

Dynamic configurations and data mapping must utilize `mediaReporting`. For more information, see [Migrate Data Prep for custom fields to the new Streaming Media fields](/help/use-cases/xdm-updates/migrate-dataprep.md).

### Other services that must be migrated

* Adobe Journey Optimizer  – Campaign and journey configurations need to incorporate mediaReporting.

* Event Forwarding – Only mediaReporting fields should be included in configurations

* Query Services – Queries must reference mediaReporting fields.

* Tags Configurations – Any tagging setups should reference mediaReporting fields.

* Connections and Destinations – Import/export data flows should be structured around mediaReporting fields.

Please be aware that any other flow that relies on `media.mediaTimed` fields is impacted and requires logic updates.

## Next Steps & Support

All customers using Adobe Data Collection for Streaming Media must complete their migrations within the designated transition period. 

For any questions or support needs, please don't hesitate to reach out to our support team.

