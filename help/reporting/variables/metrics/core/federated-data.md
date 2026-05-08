---
title: Federated data
description: Federated data flags sessions received via a federated data share rather than a customer's own implementation.
feature: Metrics
role: User, Admin
---

# Federated data

The **Federated data** flag indicates that the session was received via a federated data share rather than from the customer's own implementation (for example, when a content distributor shares playback data with a content owner). Use it to separate first-party and federated data in reports. See [Federated Media](/help/use-cases/federated-media.md) for an overview of how federated data works.

## How this metric is calculated

The media backend sets `mediaReporting.sessionDetails.isFederated = true` when the session arrives over a federated channel. The flag is reported on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.federated` to an eVar or event. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.isFederated`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A |
