---
title: AEM and Adobe Commerce Integration using Commerce Integration Framework
description: AEM and Adobe Commerce are seamlessly integrated using the Commerce Integration Framework (CIF). CIF enables AEM to access an Adobe Commerce instance and communicate with Adobe Commerce via GraphQL. It also allows AEM Authors to use Product and Category Pickers and the Product Console to browse through product and category data fetched on-demand from Adobe Commerce. In addition, CIF provides an out-of-the-box storefront that can accelerate commerce projects.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b
feature: Commerce Integration Framework
role: Admin
---
# AEM and Adobe Commerce Integration Using Commerce Integration Framework {#aem-framework}

The Experience Manager and Adobe Commerce are seamlessly integrated using the Commerce Integration Framework (CIF). CIF enables AEM to directly access and communicate with the commerce instance using Adobe Commerce's [GraphQL APIs](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
> Minimum supported GraphQL API version is 2.3.5. Certain features are only supported in newer versions or just in the Adobe Commerce edition.

>[!NOTE]
>
>GraphQL is currently used in two (separate) scenarios in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* This scenario, where CIF communicates with commerce via GraphQL.
>* [AEM Content Fragments work together with the AEM GraphQL API (a customized implementation, based on standard GraphQL), to deliver structured content for use in your applications](/help/headless/graphql-api/content-fragments.md).

## Architecture Overview {#overview}

The overall architecture is as follows:

![CIF Architecture Overview](../assets/AEM_Magento_Architecture.png)

Within CIF, there is support for server-side and client-side communication patterns.
Server-side APIs calls are implemented using the built-in, generic [GraphQL client](https://github.com/adobe/commerce-cif-graphql-client) in combination with a [set of generated data models](https://github.com/adobe/commerce-cif-magento-graphql) for the commerce GraphQL schema. Also, any GraphQL query or mutation in GQL format can be used.

For the client-side components, which are built using [React](https://reactjs.org/), the [Apollo Client](https://www.apollographql.com/docs/react/) is used.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) follow very similar design patterns and best practices as the [AEM WCM Core Components](https://github.com/adobe/aem-core-wcm-components).

The business logic and backend communication with Adobe Commerce for the AEM CIF Core Components is implemented in Sling Models. In case it is necessary to customize this logic to fulfill project-specific requirements, the delegation Pattern for Sling Models can be used.

>[!TIP]
>
>The [Customizing AEM CIF Core Components](../customizing/customize-cif-components.md) page has a detailed example and best practice on how to customize CIF Core Components.

Within projects, AEM CIF Core Components and custom project components can easily retrieve the configured client for an Adobe Commerce store associated with an AEM page via Sling Context-Aware configuration.

## Search {#search}

CIF provides out-of-the-box a [Search Core Component](https://www.aemcomponents.dev/content/core-components-examples/library/commerce/search.html) that is a server-side rendered search experience based on [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/). Commerce customers have the option to use [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html?lang=en) instead. Follow this [link](/help/commerce-cloud/integrating/live-search-plp.md) to learn more about the CIF - Live Search integration.

