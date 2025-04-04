---
title: Current Maintenance Release Notes of [!DNL Adobe Experience Manager] as a Cloud Service.
description: Current Maintenance Release Notes of [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
---

# Maintenance Release Notes {#maintenance-release-notes}

The following section outlines the technical release notes for the current maintenance release of Experience Manager as a Cloud Service.

## Release 19823 {#19823}

Summarized below are the continuous improvements for maintenance release 19823, which was publicly released on March 4, 2025. The previous maintenance release was release 19687.

The 2025.3.0 feature activation will provide the full feature set for this maintenance release. See the [Experience Manager Releases Roadmap](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) for more information.

### Enhancements {#enhancements-19823}

* ASSETS-46491: OSGI event handler for asset processing status change.
* ASSETS-45613: Send unpublish events when assets are deleted or moved.
* ASSETS-45131: Custom tag property support in Content Hub.

### Fixed Issues {#fixed-issues-19823}

* ASSETS-20433: Dynamic Media ingestion issues with password-protected PDFs.
* ASSETS-24675: Image processing options not shown for swatch-only image profile.
* ASSETS-41257: Asset version comparison renders asset with incorrect aspect ratio. Asset versions shown in incorrect order in timeline.
* ASSETS-44894: Assets view bookmarks might not be clickable.
* ASSETS-45015: Smart crop width and height set as zero if smart crop asset handle not found.
* ASSETS-45192: Reduce pulse request frequency.
* ASSETS-45724: Ensure DM upload is retried if upload job is not assigned.
* ASSETS-46425: Adobe Stock integration search issues.
* ASSETS-27400: Folder preview generator might attempt to open original.
* CQ-4358722: Handle different locale codes in Java 11 and Java 17.
* SITES-29369: Page Published/Unpublished Events triggered on Asset activation/deactivation.
* SITES-24074: Fix keyboard accessibility under unified shell.
* SITES-28058: Assets folder title not carried over to live copy.

### Known Issues {#known-issues-19823}

None.

### Deprecated Features and APIs {#deprecated-19823}

Deprecated and removed features and APIs in AEM as a Cloud Service are detailed in the [Deprecated and Removed Features and APIs](/help/release-notes/deprecated-removed-features.md) document.

### Security Fixes {#security-19823}

AEM as a Cloud Service is dedicated to optimizing your platform's security and performance. This maintenance release addresses 6 identified vulnerabilities, reinforcing our commitment to robust system protection.

### Embedded Technologies {#embedded-tech-19823}

|Technology|Version|Link|
|---|---|---|
|AEM Oak | 1.76.0|[Oak API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html)| 
|AEM SLING API | 2.27.6 |[Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html)|
|AEM HTL| 1.4.26-1.4.0 |[HTML Template Language Specification](https://github.com/adobe/htl-spec)|
|AEM Core Components| 2.27.0|[AEM WCM Core Components](https://github.com/adobe/aem-core-wcm-components)|
