---
title: Federated data
description: The Federated data dimension flags sessions received via a federated data share rather than a customer's own implementation.
feature: Dimensions
role: User, Admin
---

# Federated data

>[!AVAILABILITY]
>
>The Federated Analytics service is available only when using streaming media features with Adobe Analytics. Federated Analytics is not available in Customer Journey Analytics.

The **Federated data** dimension flags whether a session was received via a federated data share rather than from your own implementation. Use it to separate first-party sessions from partner-shared sessions when comparing engagement, completion, or quality.

See the [Federated Media](/help/use-cases/federated-media.md) use case for more information.

## How this dimension is populated

The media backend sets `mediaReporting.sessionDetails.isFederated = true` when the session arrives over a federated channel.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.federated` to an eVar. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.isFederated`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | `evar1`-`evar250`, `post_evar1`-`post_evar250` (the eVar that your processing rule maps `a.media.federated` to) |

## Dimension items

| Value | Description |
| --- | --- |
| `true` | The session was received from a federated partner. |
| (empty) | The session is from your own implementation. The field is omitted for non-federated sessions. |
