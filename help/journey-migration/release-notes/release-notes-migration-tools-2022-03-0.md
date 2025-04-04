---
title: Release Notes for Migration Tools in AEM as a Cloud Service Release 2022.3.0
description: Release Notes for Migration Tools in AEM as a Cloud Service Release 2022.3.0
feature: Release Information
exl-id: ab43605d-d46e-43de-b71f-fab610609550
role: Admin
---
# Release Notes for Migration Tools in AEM as a Cloud Service Release 2022.3.0 {#release-notes}

This page outlines the Release Notes for Migration Tools in AEM as a Cloud Service 2022.3.0.

## Best Practices Analyzer {#bpa-release}

### Release Date {#release-date-bpa}

The Release Date for Best Practices Analyzer v2.1.26 is March 16, 2022.

### What's New {#what-is-new-bpa}

* Ability to detect unprocessed assets. If unprocessed assets are detected, these assets either must be set to processed or be removed from the migration set during content transfer to avoid running into issues during content ingestion.
* Ability to detect if content has more than 1000 vanity URLs. Using a high number of vanity URLs is not best practice since it puts a load on Dispatcher and Publish servers.
* Ability to identify issues related to Oak index definitions and detect incompatibilities with AEM as a Cloud Service.
* Ability to detect and report on usage of Externalizer configurations. In AEM as a Cloud Service Externalizer, configurations are set by Cloud Manager. Therefore, existing Externalizer configurations must be refactored to maintain compatibility.

### Bug Fixes {#bug-fixes-bpa}

* In some scenarios, BPA failed to run because of FormsSelectiveFeaturesAnalysis throwing an assertion error.
* BPA was reporting findings related to the WRK pattern as MAJOR instead of CRITICAL.
* BPA was incorrectly reporting findings related to Oak index definitions in ui.apps as CRITICAL.

## Content Transfer Tool {#ctt-release}

### Release Date {#release-date-ctt}

The Release Date for Content Transfer Tool v1.9.0 is February 28, 2022.

### What's New {#what-is-new-ctt}

* Check Size Guardrails - The Content Transfer Tool Check Size feature helps reduce failed content transfers. With the Check Size feature, users can determine whether they have sufficient disk space in the `crx-quickstart` subdirectory before extraction. And, they can estimate the migration set size and verify if it's supported. If one or both these checks are violated, users see warnings in the CTT user interface. With this guardrail, you can avoid content transfer failures and proactively discuss migration options with Adobe Customer Care. See [Determining migration set size and disk space](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#migration-set-size) for more details.
