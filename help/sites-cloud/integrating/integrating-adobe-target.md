---
title: Integrating with Adobe Target
description: Learn how to integrate Adobe Target with AEM as a Cloud Service by using the Touch UI and Adobe Launch.  
feature: Integration
role: Admin
exl-id: cf243fb6-5563-427f-a715-8b14fa0b0fc2
solution: Experience Manager Sites
---
# Integrating with Adobe Target{#integrating-with-adobe-target}

As part of the Adobe Experience Cloud, Adobe Target lets you increase content relevance through targeting and measuring across all channels. Integrating Adobe Target and AEM as a Cloud Service requires:

* using the Touch UI to create a Target Configuration in AEM as a Cloud Service (IMS configuration required).
* adding and configuring Adobe Target as an extension in [Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html).

Adobe Launch is necessary for managing client-side properties for both Analytics and Target in AEM pages (JS libraries/tags). That said, the integration with Launch is needed for "Experience Targeting". 

For the export of Experience Fragments and/or Content Fragments to Target, you need the [Adobe Target Configuration](#create-configuration), including the [IMS Integration](#ims-configuration).

>[!NOTE]
>
>Customers who do not have an existing Target account, can request access to the Target Foundation Pack for Experience Cloud. The Foundation Pack provides volume limited use of Target.

## Creating the Adobe Target Configuration {#create-configuration}

1. Navigate to **Tools** → **Cloud Services**.
![Navigation](assets/cloudservice1.png "Navigation")
2. Select **Adobe Target**.
3. Select the **Create** button.
![Create](assets/tenant1.png "Create")
4. Fill in the details (see below), and select **Connect**.
![Connect](assets/open_screen1.png "Connect")

### IMS Configuration {#ims-configuration}

The integration of AEM with Adobe Target via the Target Standard API requires the configuration of Adobe IMS (Identity Management System). The Target IMS configuration must be created (after Target is provisioned). See [Setting Up IMS Integrations for AEM as a Cloud Service](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) and the video [Integrating Experience Platform Launch and AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html) to learn how to create the Target IMS configuration.

>[!NOTE]
>
>[IMS integrations are now configured with S2S OAuth](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md). 
>
>Previous configurations were made with [JWT Credentials that are now subject to deprecation in the Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md). 

>[!NOTE]
>
>When configuring the project, the product profiles displayed with depend on whether you have:
>
>* Adobe Target Standard - only **Default Workspace** is available
>* Adobe Target Premium - all available workspaces are listed, as shown below

### Adobe Target Tenant ID and Adobe Target Client Code {#tenant-client}

When configuring the Adobe Target Tenant ID and Adobe Target Client Code fields, be aware of the following:

1. For most customers, the Tenant ID and the Client Code are the same. That is, both fields contain the same information and are identical. Make sure you enter the Tenant ID in both fields.
2. For legacy purposes, you can also enter different values in the Tenant ID and the Client Code fields.

In both cases:

* By default, the Client Code (if added first) is also automatically copied into the Tenant ID field.
* If necessary, you can change the default Tenant ID set.
* Backend calls to Target are based on the Tenant ID and the client side calls to Target are based on the Client Code.

As stated previously, the first case is the most common for AEM as a Cloud Service. Either way, make sure that **both** fields contain the correct information depending on your requirements.

>[!NOTE]
>
> If you want to change an existing Target Configuration:
>
> 1. Reenter the Tenant ID.
> 2. Reconnect to Target.
> 3. Save the configuration.

### Editing the Target Configuration {#edit-target-configuration}

To edit the Target configuration, follow these steps:

1. Select an existing configuration and click **Properties**.
2. Edit the properties.
3. Select **Re-connect to Adobe Target**.
4. Select **Save and Close**.

### Adding a configuration to a site {#add-configuration}

To apply a Touch UI configuration to a site, go to: **Sites** > **Select any site page** > **Properties** > **Advanced** > **Configuration** > Select the configuration tenant.

## Integrating Adobe Target on AEM sites by using Adobe Launch {#integrate-target-launch}

AEM offers an out of the box integration with Experience Platform Launch. By adding the Adobe Target extension to Experience Platform Launch, you can use the features of Adobe Target on AEM web pages. Target libraries are only rendered by using Launch.

>[!NOTE]
>
>Existing (legacy) frameworks still work, but cannot be configured in the Touch UI. Adobe recommends you rebuild the variable mapping configurations in Launch.

As a general overview, the integration steps are:

1. Create a Launch Property
2. Add the required extensions
3. Create a Data Element(to capture context hub parameters)
4. Create a Page Rule
5. Build and Publish

### Creating a Launch Property {#create-property}

A property is a container that is filled with extensions, rules, data elements.

1. Select the **New Property** button.
2. Provide a name for your property.
3. As domain, enter the IP/host on which you want to load the launch library.
4. Select the **Save** button.
![Launchproperty](assets/properties_newproperty1.png "Launchproperty")

### Adding the required extensions {#add-extension}

**Extensions** are the container that manages the core library settings. The Adobe Target extension supports client-side implementations by using Target JavaScript SDK for the modern web, at.js. Add both the **Adobe Target** and **Adobe ContextHub** extensions.

1. Select the Extension Catalog option, and search for Target in the filter.
2. Select **Adobe Target** at.js and click on the Install option.
![Target Search](assets/search_ext1.png "Target Search")
3. Select the **Configure** button. Notice the configuration window with the Target account credentials imported, and the at.js version for this extension.
4. Select **Save** to add the Target extension to your Launch property. You should be able to see the Target extension listed under the **Installed Extensions** list.
![Save Extension](assets/configure_extension1.png "Save Extension")
5. Repeat the steps above to search for the **Adobe ContextHub** extension and install it (this extension is required for the integration with contexthub parameters, based on which targeting is done).

### Creating a Data Element {#data-element}

**Data elements** are the placeholders to which you can map context hub parameters.

1. Select **Data Elements**.
2. Select **Add Data Element**.
3. Provide the name of data element and map it to a context hub parameter.
4. Select **Save**.
![Data Element](assets/data_elem1.png "Data Element")

### Creating a Page Rule {#page-rule}

In **Rule**, it defines and orders a sequence of actions, which are run on site, to achieve targeting.

1. Add a set of actions as exemplified in the screenshot.
![Actions](assets/rules1.png "Actions")
2. In Add Params to All Mboxes, add the data element configured earlier (see data element above), to the parameter which is sent in the mbox call.
![Mbox](assets/map_data1.png "Actions")

### Build and Publish {#build-publish}

To learn how to build and publish, see [page](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html).

## Changes in content structure between Classic and Touch UI configurations {#changes-content-structure}

<table style="table-layout:auto">
  <tr>
    <th>Change</th>
    <th>Classic UI Configuration</th>
    <th>Touch UI Configuration</th>
    <th>Consequences</th>
  </tr>
  <tr>
    <td>Location of the Target Configuration.</td>
    <td>/etc/cloudservices/testandtarget/</td>
    <td>/conf/tenant/settings/cloudconfigs/target/</td>
    <td> Earlier multiple configurations were present under /etc/cloudservices/testandtarget but now a single configuration is present under a tenant.</td>
  </tr>
</table>

>[!NOTE]
>
>Legacy configurations are still supported for existing customers (without the option to edit or create). Legacy configurations are part of content-packages uploaded by customers using VSTS.
