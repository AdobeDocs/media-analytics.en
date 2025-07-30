---
title: Updated XDM fields for collecting Streaming Media data into Adobe Experience Platform
description: Learn about updated XDM fields for collecting Streaming Media data into Adobe Experience Platform
feature: Streaming Media
role: User, Admin, Data Engineer
---
# Updated XDM fields for collecting Streaming Media data into Adobe Experience Platform

We would like to inform you that our teams have officially released the new Adobe Data Collection (Analytics Source Connector) implementation for the Streaming Media service that migrates from one set of XDM fields to another. The release has been finalized on the 23rd of July.
Impact

As part of this migration, the mediaReporting XDM field group has been added to the XDM schemas used in Adobe Data Collection (Analytics Source Connector) flows. Any existing and newly generated Adobe Data Collection schema will automatically include this field.
All Adobe Data Collection (Analytics Source Connector) flows that transfer Streaming Media data from Adobe Analytics to Adobe Experience Platform (AEP) are currently sending data both on the mediaReporting and the media.mediaTimed XDM paths. We will keep this set-up up for three months, until the end of October, to provide a transition period. However, after this period, at the end of October, the media.mediaTimed fields will be fully deprecated, and data ingested after this period will only include mediaReporting. After deprecation, the media.mediaTimed fields will no longer be visible in the Adobe Experience Platform schema UI, and data ingestion on these fields will stop. Consequently, these fields will no longer be available for use in any Adobe Experience Platform service. However, data that has been already ingested before this date will remain available and customers will still be able to use it for reporting proposes. The changes are limited to Adobe Experience Platform (AEP) and do not impact Adobe Analytics, including data collection, processing, and reporting. Tools such as Data Feeds and Processing Rules remain unaffected, so no updates to the Analytics implementation are required.
If you are leveraging the Adobe Data Connector (ADC) and using CJA reports or any other AEP service on top of imported Streaming Media data, this communication is intended for you. Otherwise, please confirm that you are not using the enabled flow.
Additional differences
With the new ADC implementation for Streaming Media, keep-alive calls from Adobe Analytics are now also ingested into Adobe Experience Platform (AEP). Previously, these calls were not reflected in AEP-based tools such as Customer Journey Analytics (CJA). As a result, customers may observe:
*
Accurate session counts, which in some cases may mean deflation in session counts, since keep-alive calls help maintain active user sessions even in the absence of direct media interactions. These keep-alive calls are generated every 20 minutes after the last event per media playback, with the intent to keep the visit open. To ensure optimal session tracking in CJA, it is recommended to configure the visit expiration to 30 minutes in the Data View setup.
*
An increase in the number of events, as keep-alive calls are now counted in the CJA Events metric. Note: If you want to exclude them from reporting, you can create a filter that excludes events which have Event Type == media.keepalive.
This change ensures greater alignment between Analytics and CJA reporting.
Actions
To ensure a smooth transition, we kindly ask all customers to migrate their existing setups from media.mediaTimed fields to mediaReporting fields during the three-month migration window. The affected areas will be those that rely on media.mediaTimed usage and should be migrated as follows:
Customer Journey Analytics (CJA)
There are two ways in which CJA reports can be migrated
*
To retain historical data: Adobe teams have developed a predefined CJA template that introduces a set of derived fields that combine the old and new XDM fields into a single one. This template can be enabled per data view upon request. Please contact our support team to further assist you in enabling the new fields. Note: These derived fields will not count toward your organization's derived field limit and will be added on top of it.
*
If historical data is not required: It is enough to use the Reporting XDM Field Path at reporting time. A comprehensive documentation outlining the migration process is available in the attached files.
After choosing one of the above options, you will need to manually replace each media.mediaTimed field used in Customer Journey Analytics reports with its corresponding Derived Field or Reporting XDM Field Path.
Real-Time CDP (RT-CDP)
All Audiences and Profiles must be based on mediaReporting. Migration tutorials for both services can be found in the attached files.
Data Stream / Data Collection
Dynamic configurations and data mapping must utilize mediaReporting. A DataPrep mapping migration tutorial has also been attached.
Other services that must be migrated:
*
Adobe Journey Optimizer (AJO) – Campaign and journey configurations need to incorporate mediaReporting.
*
Event Forwarding – Only mediaReporting fields should be included in configurations
*
Query Services – Queries must reference mediaReporting fields.
*
Tags Configurations – Any tagging setups should reference mediaReporting fields.
*
Connections and Destinations – Import/export data flows should be structured around mediaReporting fields.
Please be aware that any other flow that relies on media.mediaTimed fields is impacted and requires logic updates.
Next Steps & Support
We encourage all customers using Adobe Data Collection for Streaming Media to complete their migrations within the designated transition period. A final communication will be sent prior to the full decommissioning of the previous implementation at end of October.
For any questions or support needs, please don't hesitate to reach out to our support team.