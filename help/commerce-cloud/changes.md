---
title: Notable changes of the Commerce Integration Framework (CIF) add-on
description: Notable changes of the Commerce Integration Framework (CIF) compared to old CIF versions.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
feature: Commerce Integration Framework
role: Admin
---
# Notable Changes to the Commerce Integration Framework (CIF) Add-on{#notable-changes}

Adobe Experience Manager as a Cloud Service brings many new features and possibilities to manage your AEM Projects. To learn more about these capabilities, follow the link for [changes to Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

This document highlights the important differences between the Commerce Integration Framework (CIF) add-on and old CIF versions, known as CIF Classic (Quickstart) and CIF Open-source.

## Installation & Updates

The AEM CIF add-on gets installed via Cloud Manager. Installation requires a CIF credit except for sandboxes where CIF can be installed without credits. Credits are received automatically via the provisioning of the CIF add-on in your AEM contract.

The add-on gets automatically updates as part of the regular AEM as a Cloud Service update.

**Previous CIF versions**

* CIF Classic: No installation needed, CIF was part of the Quickstart. CIF updates were part of regular AEM or service pack updates
* CIF Open-source for AEM On-premises: Installation via GitHub. Updates were part of manual update / maintenance work.
* CIF Open-source for AEM Adobe Managed Services: Installation by way of the Adobe Account Team. Updates were part of manual update / maintenance work.

## Endpoint Configuration

The endpoint gets configured and updated either via Cloud Manager UI or its CLI.

**Previous CIF versions**

* CIF Classic: Via OSGi configuration in AEM
* CIF Open-source: Via CIF Configuration Browser

## Deployment of CIF Venia Project

Project available in [Cloud Manager Git Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/integrating-with-git.html) and deployment done via [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html)

**Previous CIF versions**

* CIF Classic: By way of AEM package install
* CIF Open-source: Via [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)

## Product Catalog Data

Product catalog data get requested on-demand via real-time calls to an external endpoint that support the required GraphQL APIs. These APIs support access to live or staged data at any given date. No replication needed.

**Previous CIF versions**

* CIF Classic: Live and staged product data gets imported and persisted in JCR on AEM Author via full or delta product import. Live product data gets replicated to AEM Publish.

## Product catalog experiences with AEM rendering

AEM renders product catalog experiences on-the-fly using AEM catalog templates that have been assigned to products and categories. No replication needed.

**Previous CIF versions**

* CIF Classic: AEM Author creates an AEM page for every category / product using the catalog blueprint tool. These pages get replicated to AEM Publish.

>[!NOTE]
>
>For additional documentation on how to use CIF with AEM Managed Service or AEM On-premise, see [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
