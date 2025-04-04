---
title: Cascading metadata
description: This article describes how to define cascading metadata for assets.
contentOwner: AG
feature: Metadata
role: Admin, User
exl-id: 1d3ad496-a964-476e-b1da-4aa6d8ad53b7
---
# Cascading Metadata {#cascading-metadata}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>New</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime and Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>New</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>New</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets integration with Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>New</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI Extensibility</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>New</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Enable Dynamic Media Prime and Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Search Best Practices</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Metadata Best Practices</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media with OpenAPI capabilities</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets developer documentation</b></a>
        </td>
    </tr>
</table>

When capturing the metadata information of an asset, users provide information in the various available fields. You can display specific metadata fields or field values that are dependent on the options selected in the other fields. Such conditional display of metadata is called cascading metadata. In other words, you can create a dependency between a particular metadata field/value and one or more fields and/or their values.

Use metadata schemas to define rules for displaying cascading metadata. For example, if your metadata schema includes an asset type field, you can define a pertinent set of fields to be displayed based on the type of asset a user selects.

Here are some use cases for which you can define cascading metadata:

* Where user location is required, display relevant city names based on the user's choice of country and state.
* Load pertinent brand names in a list based on the user's choice of product category.
* Toggle the visibility of a particular field based on the value specified in another field. For example, display separate shipping address fields if the user wants the shipment delivered at a different address.
* Designate a field as mandatory based on the value specified in another field.
* Change options displayed for a particular field based on the value specified in another field.
* Set the default metadata value in a particular field based on the value specified in another field.

## Configure cascading metadata in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Consider a scenario where you want to display cascading metadata based on the type of asset that is selected. Some examples

* For a video, display applicable fields such as format, codec, duration, and so on.
* For a Word or PDF document, display fields, such as page count, author, and so on.

Irrespective of the asset type chosen, display the copyright information as a required field.

1. Select the [!DNL Experience Manager] logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. In the **[!UICONTROL Schema Forms]** page, select a schema form and then select **[!UICONTROL Edit]** from the toolbar to edit the schema.

   ![select_form](assets/select_form.png)

1. (Optional) In the metadata schema editor, create a field to conditionalize. Specify a name and property path in the **[!UICONTROL Settings]** tab.

   To create a tab, select `+` to add a tab and then add a metadata field.

   ![add_tab](assets/add_tab.png)

1. Add a Dropdown field for asset type. Specify a name and property path in the **[!UICONTROL Settings]** tab. Add an optional description.

   ![asset_type_field](assets/asset_type_field.png)

1. Key-values pairs are the options provided to a form-user. You can provide the key-value pairs either manually or from a JSON file.

    * To specify the values manually, select **[!UICONTROL Add Manually]**, and select **[!UICONTROL Add Choice]** and specify the option text and value. For example, specify Video, PDF, Word, and Image asset types.

    * To fetch the values from a JSON file dynamically, select **[!UICONTROL Add Through JSON Path]** and provide the path of the JSON file. [!DNL Experience Manager] fetches the key-value pairs in the real time when the form is presented to the user.

   Both options are mutually exclusive. You cannot import the options from a JSON file and edit manually.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >When you add a JSON file, the key-value pairs are not displayed in the metadata schema editor but are available in the published form.

   >[!NOTE]
   >
   >When adding choices, if you click the pop-up field, the interface is distorted and the delete icon for the choices stops working. Do not click the drop-down until you save the changes. If you face this issue, save the schema and open it again to continue editing.

1. (Optional) Add the other required fields. For example, format, codec, and duration for the asset type video.

   Similarly, add dependent fields for other asset types. For example, add fields page count and author for document assets, such as PDF and Word files.

   ![video_dependent_fields](assets/video_dependent_fields.png)

1. To create a dependency between the asset type field and other fields, choose the dependent field and open the **[!UICONTROL Rules]** tab.

   ![select_dependentfield](assets/select_dependentfield.png)

1. Under **[!UICONTROL Requirement]**, choose the **[!UICONTROL Required, based on new rule]** option.
1. Select **[!UICONTROL Add Rule]** and choose the **[!UICONTROL Asset Type]** field to create a dependency. Also choose the field value on which to create the dependency. In this case, choose **[!UICONTROL Video]**. Select **[!UICONTROL Done]** to save the changes.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >Dropdown with manually predefined values can be used with rules. Dropdown menus with configured JSON path can't be used with rules that use predefined values to apply conditions. If the values are loaded from JSON at runtime, it is not possible to apply a predefined rule.

1. Under **[!UICONTROL Visibility]**, choose the **[!UICONTROL Visible, based on new rule]** option.

1. Select **[!UICONTROL Add Rule]** and choose the **[!UICONTROL Asset Type]** field to create a dependency. Also choose the field value upon which to create the dependency. In this case, choose **[!UICONTROL Video]**. Select **[!UICONTROL Done]** to save the changes.

   ![define_visibilityrule](assets/define_visibilityrule.png)

   >[!CAUTION]
   >
   >To reset the values, select anywhere on the interface other than the values. If the values are reset, select the values again.

   >[!NOTE]
   >
   >You can apply **[!UICONTROL Requirement]** condition and **[!UICONTROL Visibility]** condition independent of each other.

1. Similarly, create a dependency between the value Video in the Asset Type field and other fields, such as Codec and Duration.
1. Repeat the steps to create dependency between document assets (PDF and Word) in the [!UICONTROL Asset Type] field and fields such as [!UICONTROL Page Count] and [!UICONTROL Author].
1. Click **[!UICONTROL Save]**. Apply the metadata schema to a folder.

1. Navigate to the folder to which you applied the Metadata Schema and open the properties page of an asset. Depending upon your choice in the Asset Type field, pertinent cascading metadata fields are displayed.

   ![Cascading metadata for Video asset](assets/video_asset.png)
   *Figure: Cascading metadata for Video asset*

   ![Cascading metadata for document asset](assets/doc_type_fields.png)
   *Figure: Cascading metadata for document asset*

**See also**

* [Translate Assets](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [Assets supported file formats](file-format-support.md)
* [Search assets](search-assets.md)
* [Connected assets](use-assets-across-connected-assets-instances.md)
* [Asset reports](asset-reports.md)
* [Metadata schemas](metadata-schemas.md)
* [Download assets](download-assets-from-aem.md)
* [Manage metadata](manage-metadata.md)
* [Search facets](search-facets.md)
* [Manage collections](manage-collections.md)
* [Bulk metadata import](metadata-import-export.md)
* [Publish Assets to AEM and Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
