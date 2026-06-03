---
title: App version
description: Reports the version of the media player application used for each streaming session.
feature: Dimensions
role: User, Admin
---

# App version

>[!BEGINSHADEBOX]

*This page covers the **App version** reporting dimension. See [App version](/help/implementation/variables/core/app-version.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **App version** dimension reports the version string of the media player application configured at SDK initialization. Use it to identify which player versions are in active use, correlate quality or behavioral changes with specific releases, and prioritize support for widely used versions.

>[!NOTE]
>
>This dimension captures the version of your **media player application**, not Adobe's SDK library. Adobe's own SDK library version is collected automatically as a separate internal field.

## How this dimension is populated

The app version is set once at SDK initialization and is automatically included in every session start request.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected via XDM field mapping when using Edge implementations. For Analytics-only implementations, map context data `media.sdkVersion` to a custom eVar using a [processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.md). |
| Customer Journey Analytics | [`xdm.mediaReporting.sessionDetails.appVersion`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | No dedicated data feed column. For Analytics-only implementations, use the data feed column of the custom eVar configured via processing rule. |
| Audience Manager | `c_contextdata.media.sdkVersion` (Analytics-only implementations) |

## Dimension items

Each item is the literal version string configured at SDK initialization. Use a consistent versioning scheme across your implementations so version strings roll up predictably in reports.
