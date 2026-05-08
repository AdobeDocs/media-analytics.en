---
title: Media downloaded
description: The Media downloaded dimension flags sessions that played downloaded offline content.
feature: Dimensions
role: User, Admin
---

# Media downloaded

>[!BEGINSHADEBOX]

*This page covers the **Media downloaded** reporting dimension. See [Media downloaded flag](/help/implementation/variables/core/media-downloaded-flag.md) for how to collect this variable.*

>[!ENDSHADEBOX]

The **Media downloaded** dimension flags sessions that played previously downloaded offline content rather than a live stream from the internet. Use it to separate offline playback from streamed sessions when comparing engagement, completion, or quality.

## How this dimension is populated

The downloaded flag is set by the player in one of three ways. Initialize the tracker with the flag (Mobile SDK), send the `sessionStart` to the `/downloaded` endpoint variant (Media Edge API direct), or include `media.downloaded: true` in the `sessionStart` params (Media Collection API).

| Reporting system | Source |
| --- | --- |
| Adobe Analytics | Create a [Processing rule](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/processing-rules/pr-overview) that maps `a.media.downloaded` to an eVar. |
| Customer Journey Analytics | [`mediaReporting.sessionDetails.isDownloaded`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/data-types/session-details-reporting) |
| Data feeds | N/A |

## Dimension items

| Value | Description |
| --- | --- |
| `true` | The session played downloaded offline content. |
| (empty) | The session played a live stream. The field is omitted rather than set to `false`. |
