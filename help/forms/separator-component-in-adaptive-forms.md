---
title: What is separator component in Adaptive Forms?
description: Separator component in Adaptive Forms help to visually segregate sections of a form.
feature: Adaptive Forms, Foundation Components
role: User
exl-id: 1b7857f9-b201-43ca-870d-42a09c441d9a
---
# Separator component in Adaptive Forms{#separator-component-in-adaptive-forms}

You can use the separator component to visually segregate panels of a form. You can define the overall appearance and style of a separator component by specifying the following properties of the separator component:

* **Element Name:** Specifies the name of the component. The SOM expressions address the component with a value specified in the Element Name field.
* **Thickness:** Specifies the thickness of the separator component in pixels.

* **CSS Class:** Specifies the custom CSS class for the separator component  

* **Inline styles:** With [!DNL AEM Forms], you can now apply inline CSS styles to individual Adaptive Form components and preview the changes in real-time.

You can use the Layout mode to define the number of columns that the separator component spans to. For more information, see [Use Layout mode to resize components](resize-using-layout-mode.md).

To specify the properties of a separator component:

1. Select a separator component and select ![cmppr](assets/cmppr.png). The properties open in the sidebar.
1. Click a tab in the Inline CSS Properties section so you can specify CSS properties. For example, a. In the Field tab, click **Add Item**. A row with two fields gets added.
1. In the first field from the left, specify a CSS3 property you want to apply. For example, **border**. You can also select a property by clicking the down-arrow button. The drop-down list is not exhaustive and you can specify any supported CSS3 property name in this field.
1. In the adjoining field, specify a valid value for the specified CSS3 property. For example, **3 pixels solid black**.
1. Click **Add Item** to specify another property and its value.
1. Click **Preview** so you can see the changes in the form.
1. Do one of the following:
    * Confirm the changes by clicking **OK**
    * Exit the dialog box without any changes by clicking **Cancel**.
