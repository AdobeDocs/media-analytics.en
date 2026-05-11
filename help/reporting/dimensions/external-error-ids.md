---
title: External error IDs
description: The External error IDs dimension reports unique error identifiers from external sources such as CDN errors.
feature: Dimensions
role: User, Admin
---

# External error IDs

The **External error IDs** dimension reports unique error identifiers from any source outside the player SDK (for example, CDN errors). The player must provide the codes or IDs at implementation time via the error tracking API. Multiple error IDs per session are supported.

## How this dimension is populated

The player passes external error IDs to the tracker on `media.error` events. The backend collects unique IDs across the session and reports them on the close call.

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Automatically collected from context data `a.media.qoe.externalErrors` when [[!UICONTROL Media Quality]](/help/reporting/media-reports-enable.md) is enabled. |
| Customer Journey Analytics | [`mediaReporting.qoeDataDetails.externalErrors`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/qoe-data-details-reporting) |
| Data feeds | `videoqoeextneralerrors` |

## Dimension items

Each item is an error code or ID provided by the player. Use a stable taxonomy across implementations so error IDs roll up correctly across sessions.
