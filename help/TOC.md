---
product: adobe analytics
audience: end-user
user-guide-title: Adobe Analytics for Streaming Media
breadcrumb-title: Media Analytics Guide
user-guide-description: Implement Adobe Analytics for Streaming Media. Includes the Media SDK and the Media Collection API.
sub-product: media analytics
---

# Adobe Analytics for Streaming Media {#using}

+ [Streaming Media Analytics Guide](media-overview.md)
+ Release Notes {#release-notes}
  + [Streaming Media Release Notes](additional-resources/release-notes.md)
+ Getting Started {#getting-started}
  + [Overview](getting-started/getting-started.md)
  + [Prerequisites](getting-started/prereqs.md)
  + [Supported devices](getting-started/supported-devices.md)
  + [Streaming Media Documentation](getting-started/implementation-documentation.md)
  + [SDKs, Libraries, and Extensions](getting-started/download-sdks.md)
  + End of Support {#end-of-support}
    + [Media Analytics Mobile SDK End of Support](additional-resources/end-of-support-faqs.md)
    + Legacy - Standalone Media SDK to Launch Migration {#sdk-to-launch}
      + [Overview](legacy/sdk-to-launch/sdk-to-launch-migration.md)
      + [Android - Media SDK to Launch](legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-android.md)
      + [iOS - Media SDK to Launch](legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-ios.md)
      + [JavaScript - Media SDK to Launch](legacy/sdk-to-launch/sdk-to-launch-migration-platforms/sdk-to-launch-migration-js.md)  
+ Implementation {#implementation}
  + [Implementation overview](implementation/overview.md)
  + Edge implementations (recommended) {#edge-recommended}
    + Media Edge SDKs / Extension {#media-edge-sdk}
      + [Media Edge SDKs / Extension setup](/help/implementation/edge/implementation-edge.md)
      + [Media Edge Mobile SDKs](/help/implementation/edge/edge-mobile-sdk.md)
    + [Media Edge API](/help/implementation/edge/implementation-edge-api.md)
  + Adobe Analytics-only implementations {#analytics-only}
    + Media SDKs / Extension {#media-sdk}
      + [JavaScript Web SDK](implementation/media-sdk/setup/web-implementation.md)
      + [Media Analytics extension](implementation/media-sdk/setup/web-implementation-tags.md)
      + [Mobile SDKs](implementation/media-sdk/setup/mobile-implementation.md)
      + OTT SDKs {#ott-setup}
        + [Install the Chromecast SDK](implementation/media-sdk/setup/set-up-chromecast.md)
        + [Install the Roku SDK](implementation/media-sdk/setup/set-up-roku.md)
    + Media Collection APIs - Implementation {#streaming-media-apis}
      + [Media Collection](implementation/media-collection-api/mc-api-overview.md)
      + [API Quick Start](implementation/media-collection-api/mc-api-impl/mc-api-quick-start.md)
      + [Sessions Request](implementation/media-collection-api/mc-api-ref/mc-api-sessions-req.md)
      + [Events Request](implementation/media-collection-api/mc-api-ref/mc-api-events-req.md)
      + [Request Parameters](implementation/media-collection-api/mc-api-ref/mc-api-req-params.md)
      + [Event Types and Descriptions](implementation/media-collection-api/mc-api-ref/mc-api-event-types.md)
      + Implementing the API {#mc-api-impl}
        + [Setting the HTTP Request Type in Your Player](implementation/media-collection-api/mc-api-impl/mc-api-set-http-req.md)
        + [Obtaining a Session ID](implementation/media-collection-api/mc-api-impl/mc-api-obtain-sid.md)
        + [Implementing an Events Request](implementation/media-collection-api/mc-api-impl/mc-api-impl-events-req.md)
        + [JSON Validation Schemas](implementation/media-collection-api/mc-api-ref/mc-api-json-validation.md)
        + [Validating Event Requests](implementation/media-collection-api/mc-api-impl/mc-api-validate-reqs.md)
        + [Sending Ping Events](implementation/media-collection-api/mc-api-impl/mc-api-sed-pings.md)
        + [Sending QoE Data](implementation/media-collection-api/mc-api-impl/mc-api-sending-qoe.md)
        + [Custom Metadata Support](implementation/media-collection-api/mc-api-impl/mc-api-custom-meta.md)
        + [Timeout Conditions](implementation/media-collection-api/mc-api-impl/mc-api-timeout.md)
        + [Controlling the Order of Events](implementation/media-collection-api/mc-api-impl/mc-api-ctrl-order.md)
        + [Queueing Events When Sessions Response is Slow](implementation/media-collection-api/mc-api-impl/mc-api-queuing.md)
  + Variables {#variables}
    + [Streaming Media Parameters](implementation/variables/audio-video-parameters.md)
    + [Ad Parameters](implementation/variables/ad-parameters.md)
    + [Chapter Parameters](implementation/variables/chapter-parameters.md)
    + [Player State Parameters](implementation/variables/player-state-parameters.md)
    + [Quality Parameters](implementation/variables/quality-parameters.md)
    + [Calculated Metrics](implementation/variables/calculated-metrics.md)
+ Reporting {#media-reports}
  + [Media Reports Enablement](reporting/media-reports-enable.md)
  + [About Segments](reporting/segments.md)
  + Media Default Reports {#media-default-reports}  
    + [Default Reports Overview](reporting/reports-and-analytics/default-reports-overview.md)
    + [Media Overview](reporting/reports-and-analytics/media-reports-overview.md)  
    + [Media Detail](reporting/reports-and-analytics/media-reports-detail.md)  
    + [Media Daypart report](reporting/reports-and-analytics/media-reports-daypart.md)  
    + [Media Concurrent Viewers report](reporting/reports-and-analytics/media-concurrent-viewers-reports.md)
  + Media Workspace Panels {#media-workspace-panels}  
    + [Media Average Minute Audience panel](reporting/workspace/average-minute-audience.md)
    + [Media Concurrent Viewers panel](reporting/workspace/media-concurrent-viewers-overview.md)
    + [Media Playback Time Spent panel](reporting/workspace/media-playback-time-spent.md)
  + [Media Workspace Templates](reporting/workspace/media-workspace-templates.md)
  + [Get Concurrent Viewers Data via API](reporting/reports-and-analytics/get-concurrent-json20.md)
  + [Get Media Playback Time Spent Data via API](reporting/reports-and-analytics/get-mediaplaybacktimespent-json20.md)  
+ Use Cases {#media-use-cases}
  + [Media SDK Use Cases](use-cases/cookbook/sdk-cookbook-overview.md)
  + Player State Tracking {#player-state-tracking}
    + [Overview](use-cases/player-state-tracking/player-state-overview.md)
    + [Standard and custom states](use-cases/player-state-tracking/standard-and-custom-states.md)
    + [Implementation and reporting](use-cases/player-state-tracking/implementation-and-reporting.md)
    + [Multiple player states tracking](use-cases/player-state-tracking/multiple-player-states.md)
    + [Player state tracking examples](use-cases/player-state-tracking/player-state-examples.md)
  + [Track Offline Downloaded Content](use-cases/track-downloaded-content.md)
  + [Federated Analytics](use-cases/federated-analytics.md)
  + [Handling application interrupts during playback](use-cases/cookbook/app-interrupts.md)
  + [Media Stream Attribution](use-cases/media-analytics-cookbook/media-dimensions.md)
  + [Resuming inactive sessions](use-cases/cookbook/resuming-inactive.md)
  + [Roku Tracking in SceneGraph](use-cases/cookbook/sdk-track-scenegraph.md)
  + [Handing Gaps Between Ads](use-cases/cookbook/fix-ad-play-ad.md)
  + Timelines {#timelines}
    + [Chapter start and end](use-cases/timelines/chapter-start-end.md)
    + [View to content end](use-cases/timelines/view-to-end-of-content.md)
    + [Abandon session](use-cases/timelines/user-abandons-session.md)
  + Use Analytics in OTT Apps {#analytics-with-ott}
    + [Track App States](use-cases/analytics-with-ott/track-app-states.md)
    + [Track App Actions](use-cases/analytics-with-ott/track-app-actions.md)
    + [Set User IDs](use-cases/analytics-with-ott/set-user-ids.md)
    + [OTT and Audience Manager](use-cases/analytics-with-ott/ott-am.md)
    + [OTT and Experience Cloud](use-cases/analytics-with-ott/ott-experience-cloud.md)
+ Tracking {#tracking}
  + Tracking {#track-av-playback}
    + [Overview](use-cases/track-av-playback/track-core-overview.md)
    + Track Core Streaming Media Playback {#track-core}
      + [Track Core Playback on JavaScript 3.x](use-cases/track-av-playback/track-core/track-core-javascript/track-core-js3.md)
      + [Track Core Playback on Chromecast](use-cases/track-av-playback/track-core/track-core-chromecast.md)
      + [Track Core Playback on Roku](use-cases/track-av-playback/track-core/track-core-roku.md)
    + Track Buffering {#track-buffering}
      + [Track Buffering on JavaScript 3.x](use-cases/track-av-playback/track-buffering/track-buffering-js/track-buffering-js3.md)
      + [Track Buffering on Chromecast](use-cases/track-av-playback/track-buffering/track-buffering-chromecast.md)
      + [Track Buffering on Roku](use-cases/track-av-playback/track-buffering/track-buffering-roku.md)
    + Track Seeking {#track-seeking}
      + [Track Seeking on JavaScript 3.x](use-cases/track-av-playback/track-seeking/track-seeking-js/track-seeking-js3.md)
      + [Track Seeking on Chromecast](use-cases/track-av-playback/track-seeking/track-seeking-chromecast.md)
      + [Track Seeking on Roku](use-cases/track-av-playback/track-seeking/track-seeking-roku.md)
    + Implement Standard Metadata {#impl-std-metadata}
      + [Implement standard metadata on JavaScript 3.x](use-cases/track-av-playback/impl-std-metadata/impl-std-md-js/impl-std-metadata-js3.md)
      + [Implement standard metadata on Chromecast](use-cases/track-av-playback/impl-std-metadata/impl-std-metadata-chromecast.md)
      + [Standard Metadata Parameters - Chromecast](use-cases/track-av-playback/impl-std-metadata/chromecast-metadata.md)
      + [Implement standard metadata on Roku](use-cases/track-av-playback/impl-std-metadata/impl-std-metadata-roku.md)
      + [Standard Metadata Parameters - Roku](use-cases/track-av-playback/impl-std-metadata/roku-metadata.md)
    + Track Ads {#track-ads}
      + [Overview](use-cases/track-ads/track-ads-overview.md)
      + [Track Ads on JavaScript 3.x](use-cases/track-ads/track-ads-js/track-ads-js3.md)
      + [Track Ads on Chromecast](use-cases/track-ads/track-ads-chromecast.md)
      + [Track Ads on Roku](use-cases/track-ads/track-ads-roku.md)
      + Implement Standard ad Metadata {#impl-std-ad-metadata}
        + [Implement standard ad metadata on JavaScript 3.x](use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-md-js/impl-std-ad-metadata-js3.md)
        + [Implement standard ad metadata on Roku](use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-metadata-roku.md)
    + Track Chapters and Segments {#track-chapters}
      + [Overview](use-cases/track-chapters/track-chapters-overview.md)
      + [Track Chapters and Segments on JavaScript 3.x](use-cases/track-chapters/track-chapters-js/track-chapters-js3.md)
      + [Track Chapters and Segments on Chromecast](use-cases/track-chapters/track-chapters-chromecast.md)
      + [Track Chapters and Segments on Roku](use-cases/track-chapters/track-chapters-roku.md)
    + Track Quality of Experience {#track-qos}
      + [Overview](use-cases/track-qos/track-qos-overview.md)
      + [Track Quality of Experience on JavaScript 3.x](use-cases/track-qos/track-qos-js/track-qos-js3.md)
      + [Track Quality of Experience on Chromecast](use-cases/track-qos/track-qos-chromecast.md)
      + [Track Quality of Experience on Roku](use-cases/track-qos/track-qos-roku.md)
    + Track Errors {#track-errors}
      + [Overview](use-cases/track-errors/track-errors-overview.md)
      + [Track Errors on JavaScript 3.x](use-cases/track-errors/track-errors-js/track-errors-js3.md)
      + [Track Errors on Chromecast](use-cases/track-errors/track-errors-chromecast.md)
      + [Track Errors on Roku](use-cases/track-errors/track-errors-roku.md)
+ Privacy and Security {#streaming-media-privacy}
    + [Opt-out and Privacy Settings](privacy/opt-out-privacy.md)
    + [Security](privacy/security.md)
+ Legacy Implementations {#legacy-implementations}
  + [Legacy - Overview](legacy/setup/legacy-setup-overview.md)
  + [Legacy — Download SDKs](legacy/legacy-download-sdks.md)
  + Legacy - Media SDKs {#legacy-media-sdks}
    + [Legacy - Media SDK Overview](legacy/media-sdk/setup/setup-overview.md)
    + [Set up Android](legacy/media-sdk/setup/set-up-android.md)
    + [Set up iOS](legacy/media-sdk/setup/set-up-ios.md)
    + Set up JavaScript {#setup-javascript}
      + [Set up JavaScript 2.x](legacy/media-sdk/setup/setup-javascript/set-up-js-2.md)
  + [About Heartbeat Measurement](legacy/heartbeat-measurement.md)
  + [Adobe Primetime and Streaming Media Analytics](legacy/intro-to-ava/implementation-paths/primetime-path.md)
  + [Adobe Audience Management Enablement](legacy/intro-to-ava/am-enablement.md)
  + [Custom Link Implementation](legacy/measurement-options/cl-in-aa/cl-impl-guide.md)
  + Legacy Milestone Tracking {#legacy-milestone-tracking}
    + [Legacy Milestone Tracking](legacy/measurement-options/mm-milestone-tracking/milestone-overview.md)
    + [Migrate Milestone to VA](legacy/measurement-options/mm-milestone-tracking/migrate-ms-to-va.md)
    + [Migrate Milestone to CL](legacy/measurement-options/mm-milestone-tracking/migrate-ms-to-cl.md)
  + Validation {#validation}
    + [Validation Overview](legacy/validation/validation-overview.md)
    + [Test 1: Standard Playback](legacy/validation/test1-standard-playback.md)
    + [Test 2: Media Interruption](legacy/validation/test2-media-interrupt.md)
    + [Test Call Details](legacy/validation/test-call-details.md)
    + [Heartbeat Parameter Descriptions](legacy/validation/heartbeat-params.md)
    + Debugging {#debugging}
      + [SDK Debugging](legacy/validation/debugging/sdk-debugging.md)
  + [Legacy Migration: VHL 1.x to VHL 2.x](legacy/va-1x-to-2x/mig-1x-2x-overview.md)
  + [Code Comparison v1.x to v2.x](legacy/va-1x-to-2x/code-comparison-1x-2x.md)
  + [Tracking APIs 1x to 2x](legacy/va-1x-to-2x/1x-2x-api-change.md)
  + [Legacy - Intro to AVA](legacy/intro-to-ava/implementation-paths/implementation-paths.md)
  + [Client Side Path](legacy/intro-to-ava/implementation-paths/client-side-path.md)
  + Legacy Tracking {#track-av-playback}
    + [Track Core Playback on Android](use-cases/track-av-playback/track-core/track-core-android.md)
    + [Track Core Playback on iOS](use-cases/track-av-playback/track-core/track-core-ios.md)
    + Track Core Playback on JavaScript {#track-core-javascript}
      + [Track Core Playback on JavaScript 2.x](use-cases/track-av-playback/track-core/track-core-javascript/track-core-js.md)
      + [Track Buffering on Android](use-cases/track-av-playback/track-buffering/track-buffering-android.md)
      + [Track Buffering on iOS](use-cases/track-av-playback/track-buffering/track-buffering-ios.md)
      + Track Buffering on JavaScript {#track-buffering-js}
        + [Track Buffering on JavaScript 2.x](use-cases/track-av-playback/track-buffering/track-buffering-js/track-buffering-js.md)
      + [Track Seeking on Android](use-cases/track-av-playback/track-seeking/track-seeking-android.md)
      + [Track Seeking on iOS](use-cases/track-av-playback/track-seeking/track-seeking-ios.md)
      + Track Seeking on JavaScript {#track-seeking-js}
        + [Track Seeking on JavaScript 2.x](use-cases/track-av-playback/track-seeking/track-seeking-js/track-seeking-js.md)
      + [Implement standard metadata on Android](use-cases/track-av-playback/impl-std-metadata/impl-std-metadata-android.md)
      + [Implement standard metadata on iOS](use-cases/track-av-playback/impl-std-metadata/impl-std-metadata-ios.md)
      + [iOS Metadata Keys](use-cases/track-av-playback/impl-std-metadata/ios-metadata-keys.md)
      + Implement Standard Metadata on JavaScript {#impl-std-md-js}
        + [Implement standard metadata on JavaScript 2.x](use-cases/track-av-playback/impl-std-metadata/impl-std-md-js/impl-std-metadata-js.md)
    + Track Ads {#track-ads}
      + [Track Ads on Android](use-cases/track-ads/track-ads-android.md)
      + [Track Ads on iOS](use-cases/track-ads/track-ads-ios.md)
      + Track Ads on JavaScript {#track-ads-js}
        + [Track Ads on JavaScript 2.x](use-cases/track-ads/track-ads-js/track-ads-js.md)
        + [Implement standard ad metadata on Android](use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-metadata-android.md)
        + [Implement standard ad metadata on iOS](use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-metadata-ios.md)
        + Implement Standard ad Metadata on JavaScript {#impl-std-ad-md-js}
          + [Implement standard ad metadata on JavaScript 2.x](use-cases/track-ads/impl-std-ad-metadata/impl-std-ad-md-js/impl-std-ad-metadata-js.md)
    + Track Chapters and Segments {#track-chapters}
      + [Track Chapters and Segments on Android](use-cases/track-chapters/track-chapters-android.md)
      + [Track Chapters and Segments on iOS](use-cases/track-chapters/track-chapters-ios.md)
      + Track Chapters and Segments on JavaScript {#track-chapters-js}
        + [Track Chapters and Segments on JavaScript 2.x](use-cases/track-chapters/track-chapters-js/track-chapters-js.md)
      + [Track Quality of Experience on Android](use-cases/track-qos/track-qos-android.md)
      + [Track Quality of Experience on iOS](use-cases/track-qos/track-qos-ios.md)
      + Track Quality of Experience on JavaScript {#track-qos-js}
        + [Track Quality of Experience on JavaScript 2.x](use-cases/track-qos/track-qos-js/track-qos-js.md)
    + Track Errors {#track-errors}
      + [Track Errors on Android](use-cases/track-errors/track-errors-android.md)
      + [Track Errors on iOS](use-cases/track-errors/track-errors-ios.md)
      + Track Errors on JavaScript {#track-errors-js}
        + [Track Errors on JavaScript 2.x](use-cases/track-errors/track-errors-js/track-errors-js.md)
    + Tracking Scenarios {#tracking-scenarios}
      + [VOD playback with no ads](use-cases/tracking-scenarios/vod-no-intrs-details.md)
      + [VOD playback with pre-roll ads](use-cases/tracking-scenarios/vod-preroll-ads.md)
      + [VOD playback with skipped ads](use-cases/tracking-scenarios/vod-skipped-ads.md)
      + [VOD playback with one chapter](use-cases/tracking-scenarios/vod-one-chapter.md)
      + [VOD playback with a skipped chapter](use-cases/tracking-scenarios/vod-skipped-chapter.md)
      + [VOD playback with seeking in the main content](use-cases/tracking-scenarios/vod-seeking.md)
      + [VOD playback with buffering](use-cases/tracking-scenarios/vod-buffering.md)
      + [VOD multiple trackers in parallel](use-cases/tracking-scenarios/vod-multi-trackers.md)
      + [VOD one tracker for multiple sessions](use-cases/tracking-scenarios/vod-multi-track-one-session.md)
      + [Live main content](use-cases/tracking-scenarios/live-main-content.md)
      + [Live main content with sequential tracking](use-cases/tracking-scenarios/live-sequential.md)
