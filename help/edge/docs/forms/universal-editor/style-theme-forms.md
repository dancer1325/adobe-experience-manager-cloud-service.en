---
title: Customize theme and style for an Edge Delivery Services for AEM Forms
description: Effectively customize the theme and style for AEM Forms delivered via Edge Delivery Services, ensuring a cohesive and branded user experience.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
---
# Customize the look of your forms

<span class="preview"> This feature is available through the early access program. To request access, send an email with your GitHub organization name and repository name from your official address to <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> . For example, if the repository URL is https://github.com/adobe/abc, the organization name is adobe and the repository name is abc.</span> 


Forms are crucial for user interaction on websites, allowing them to input data. You can use Cascading Style Sheets (CSS) to style fields of a form, enhancing the visual presentation of your forms, and improving the user experience. 

The Adaptive Forms Block produces a consistent structure for all form fields. The consistent structure makes it easier to develop CSS Selectors to select and style form fields based on field type and field names. 

This document outlines the HTML Structure for various form components, helps you build an understanding of how to create CSS Selectors for various form fields to style form fields of an Adaptive Forms Block. 

By the end of the article:

* You build an understanding of the structure of the default CSS file included with Adaptive Forms Block. 
* You build an understanding of the HTML structure of the form components provided by the Adaptive Forms Block, including general components and specific components like dropdowns, radio groups, and checkbox groups.
* You learn how to style form fields based on field type and field names using CSS Selectors, allowing for consistent or unique styling based on requirements.

## Understanding Form Field Types

Before diving into styling, let's review the common form [field types](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) supported by the Adaptive Forms Block:

* Input Fields: These include text inputs, email inputs, password inputs, and more.
* Checkbox Groups: Used for selecting multiple options.
* Radio Groups: Used for selecting only one option from a group.
* Dropdowns: Also known as select boxes, used for selecting one option from a list.
* Panels/Containers: Used to group related form elements together.

## Basic Styling Principles

Understanding [fundamental CSS concepts](https://www.w3schools.com/css/css_intro.asp) is crucial before styling specific form fields:

* [Selectors](https://www.w3schools.com/css/css_selectors.asp): CSS Selectors allow you to target specific HTML elements for styling. You can use element selectors, class selectors, or ID selectors.
* [Properties](https://www.w3schools.com/css/css_syntax.asp): CSS properties define the visual appearance of elements. Common properties for styling form fields include color, background-color, border, padding, margin, and more.
* [Box Model](https://www.w3schools.com/css/css_boxmodel.asp): The CSS box model describes the structure of HTML elements as a content area surrounded by padding, borders, and margins.
* Flexbox/Grid: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp) and [Grid layouts](https://www.w3schools.com/css/css_grid.asp) are powerful tools for creating responsive and flexible designs.


## Styling a form for Adaptive Forms Block

The Adaptive Forms Block offers a standardized HTML structure, simplifying the process of selecting and styling form components:

  * **Update default styles**: You can modify the default styles of a form by editing the `/blocks/form/form.css file`. This file provides comprehensive styling for a form, supporting multi-step wizard forms. It emphasizes using custom CSS variables for easy customization, maintenance, and uniform styling across forms.

  * **CSS Styling for Forms**: To ensure that your styles are applied correctly, wrap your form-specific CSS within the `main .form form` selector. This ensures that your styles target only the form elements within the main content area, avoiding conflicts with other parts of the website.
    Example:

    ```css
      main .form form input {
          /* Add styles specific to input fields inside the form */
      }

      main .form form button {
          /* Add styles specific to buttons inside the form */
      }

      main .form form label {
          /* Add styles specific to labels inside the form */
      }


## Components Structure 

The Adaptive Forms Block offers a consistent HTML structure for various form elements, ensuring easier styling and management. You can manipulate the components using CSS for styling purposes.

### General Components (except dropdowns, radio groups, and checkbox groups):

All form fields, except for dropdowns, radio groups, and checkbox groups, has the following HTML structure:

+++ HTML Structure of General Components

```HTML

  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     <label for="{FieldId}" class="field-label">First   Name</label>
     <input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>

```

  * Classes: The div element has several classes for targeting specific elements and styling. You require the `{Type}-wrapper` or `field-{Name}` classes to develop a CSS Selector to style a form field:
  * {Type}: Identifies the component by field type. For example, text (text-wrapper), number (number-wrapper), date (date-wrapper).
  * {Name}: Identifies the component by name. The name of the field can have only alphanumeric characters, the multiple consecutive dashes in the name are replaced with a single dash `(-)`, and starting and ending dashes in a field name are removed. For example, first-name (field-first-name field-wrapper).
  * {FieldId}: It is a unique identifier for the field, automatically generated.
  * {Required}: It is a boolean indicating if the field is required.
  * Label: The `label` element provides a descriptive text for the field and associates it with the input element using the `for` attribute.
  * Input: The `input` element defines the type of data to be entered. For example, text, number, email.
  * Description (Optional): The `div` with class `field-description` provides additional information or instructions for the user.

**Example of HTML Structure**

```HTML

<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>

```

+++

+++ CSS Selector for General Components

```CSS
  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper  {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper input {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target any element with the class field-{Name}  */
  main .form form .field-{Name} {
    /* Add your styles here */
    /* This could be used for styles specific to all elements with   field-{Name} class, not just inputs */
  }
  
  ```
  * `.{Type}-wrapper`: Targets the outer `div` element based on    the field type. For example, `.text-wrapper` targets all text    fields.
  * `.field-{Name}`: Further selects the element based on the specific field name. For example, `.field-first-name` targets the "First Name" text field. While this selector can be used for targeting elements with the field-{Name} class, it's important to be cautious. In this specific case, it wouldn't be useful for styling input fields because it would target not only the input itself but also the label and description elements. It's recommended to use more specific selectors like the ones you have for targeting text input fields (.text-wrapper input).

**Example CSS Selectors for General Components**

```CSS

/*Target all text input fields */
main .form form .text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  color: red;
}

/*Target all fields with name first-name*/
main .form form .field-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

```

+++

### Dropdown Component

For dropdown menus, the `select` element is used instead of an `input` element:

+++ HTML Structure of Dropdown Component

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>

```

**Example HTML Structure**

```HTML

<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  <label for="country" class="field-label">Country</label>
  <select id="country" name="country">
    <option value="">Select Country</option>
    <option value="US">United States</option>
    <option value="CA">Canada</option>
  </select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>

```

+++

+++ CSS Selectors for dropdown component

The following CSS lists some example CSS Selectors for dropdown components.

```CSS

/* Target the outer wrapper */
main .form form .drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
main .form form .drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

```
   * Target the Wrapper: The first selector (`.drop-down-wrapper`) targets the outer wrapper element, ensuring styles apply to the entire dropdown component.
   * Flexbox Layout: Flexbox arranges the label, dropdown, and description vertically for a clean layout.
   * Label Styling: The label stands out with bolder font weight and a slight margin.
   * Dropdown Styling: The `select` element receives a border, padding, and rounded corners for a polished look.
   * Background Color: A consistent background color is set for visual harmony.
   * Arrow Customization: Optional styles hide the default dropdown arrow and create a custom arrow using a Unicode character and positioning.

+++

---

### Radio Groups

Similar to dropdown components, radio groups have their own HTML structure and CSS structure:

+++ HTML Structure of Radio Group 

```HTML

<fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>

```

**Example HTML Structure**

```HTML

<fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  <legend for="color_preference" class="field-label">Favorite Color:</legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      <input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      <label for="color_red" class="field-label">Red</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      <label for="color_green" class="field-label">Green</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      <label for="color_blue" class="field-label">Blue</label>
    </div>
  <% end for %>
</fieldset>

```

+++

+++ CSS Selectors for Radio Groups

* Targeting the Fieldset

```CSS

  main .form form .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }

```
This selector targets any fieldset with the class radio-group-wrapper. This would be useful for applying general styles to the entire radio group.

* Targeting Radio Button Labels

```CSS

main .form form .radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }

```

* Target all radio button labels within a specific fieldset based on its name

```CSS

main .form form .field-color .radio-wrapper label {
  /* Your styles here */
}

```

+++

### Checkbox Groups

+++ HTML Structure of Checkbox Group 

```HTML

<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>

```

**Example HTML Structure**

```HTML

<fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  <legend for="topping_preference" class="field-label">Pizza Toppings:</legend>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_pepperoni" class="field-label">Pepperoni</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_mushrooms" class="field-label">Mushrooms</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_onions" class="field-label">Onions</label>
  </div>
</fieldset>

```

+++

+++ CSS Selectors for checkbox groups

* Targeting the outer wrapper: These selectors target the outermost containers of both radio and checkbox groups, allowing you to apply general styles to the entire group structure. This is useful for setting spacing, alignment, or other layout-related properties.

```CSS
  
  /* Targets radio group wrappers */
  main .form form .radio-group-wrapper {
    margin-bottom: 20px; /* Adds space between radio groups */  
  }

  /* Targets checkbox group wrappers */
  main .form form .checkbox-group-wrapper {
    margin-bottom: 20px; /* Adds space between checkbox groups */
  }

```

* Targeting Group Labels: This selector targets the `.field-label` element within both radio and checkbox group wrappers. This allows you to style the labels specifically for these groups, potentially making them stand out more.

```CSS

main .form form .radio-group-wrapper legend,
main .form form .checkbox-group-wrapper legend {
  font-weight: bold; /* Makes the group label bold */
}

```

* Targeting Individual Inputs and Labels: These selectors provide more granular control over individual radio buttons, checkboxes, and their associated labels. You can use these to adjust sizing, spacing, or apply more distinct visual styles.

```CSS

/* Styling radio buttons */
main .form form .radio-group-wrapper input[type="radio"] {
  margin-right: 5px; /* Adds space between the input and its label */
}

/* Styling radio button labels */
main .form form .radio-group-wrapper label {
  font-size: 15px; /* Changes the label font size */
}

/* Styling checkboxes */
main .form form .checkbox-group-wrapper input[type="checkbox"] {
  margin-right: 5px; /* Adds space between the input and its label */
}

/* Styling checkbox labels */
main .form form .checkbox-group-wrapper label {
  font-size: 15px; /* Changes the label font size */
}

```

* Customizing the Appearance of Radio Buttons and Checkboxes: This technique hides the default input and uses `:before` and `:after` pseudo-elements to create custom visuals that change appearance based on the 'checked' state.

```CSS

/* Hide the default radio button or checkbox */
main .form form .radio-group-wrapper input[type="radio"],
main .form form .checkbox-group-wrapper input[type="checkbox"] {
  opacity: 0;
  position: absolute;
}

/* Create a custom radio button */
main .form form .radio-group-wrapper input[type="radio"] + label::before {
  /* ... styles for custom radio button ... */
}

main .form form .radio-group-wrapper input[type="radio"]:checked + label::before {
  /* ... styles for checked radio button ... */
}

/* Create a custom checkbox */
main .form form .checkbox-group-wrapper input[type="checkbox"] + label::before {
  /* ... styles for custom checkbox ... */
}

main .form form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
  /* ... styles for checked checkbox ... */
}

```

+++

### Panel/Container components

+++ HTML Structure of Panel/Container components

```HTML

<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
</fieldset>

```

**Example HTML Structure**

```HTML

<fieldset class="panel-wrapper field-login field-wrapper">
  <legend for="login" class="field-label" data-visible="false">Login Information</legend>
  <div class="text-wrapper field-username field-wrapper">
    <label for="username" class="field-label">Username</label>
    <input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    <label for="password" class="field-label">Password</label>
    <input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
</fieldset>

```

* The fieldset element acts as the panel container with the class panel-wrapper and additional classes for styling based on the panel name (field-login).
* The legend element (<legend>) serves as the panel title with the text "Login Information" and the class field-label. The data-visible="false" attribute can be used with JavaScript to control the visibility of the title.
* Inside the fieldset, multiple.{Type}-wrapper elements (.text-wrapper and .password-wrapper in this case) represent individual form fields within the panel.
* Each wrapper contains a label, input field, and description, similar to the previous examples.

+++ 

+++ Example CSS Selectors for Panel/Container components

1. Targeting the Panel:

  ```CSS
    /* Target the entire panel container */
    main .form form .panel-wrapper {
      /* Add your styles here (e.g., border, padding, background color) */
      border: 1px solid #ccc;
      padding: 15px;
      border-radius: 4px;
      margin-bottom: 20px;
   }


  ```

  * The `.panel-wrapper` selector styles all elements with the class panel-wrapper, creating a consistent look for all panels.

1. Targeting the Panel Title:

  ```CSS
    /* Target the legend element (panel title) */
    .panel-wrapper legend {
      /* Add your styles here (e.g., font-weight, font-size) */
      font-weight: bold;
      font-size: 16px;
      padding-bottom: 5px;
      margin-bottom: 10px;
      border-bottom: 1px solid #ddd; /* Optional: create a separation line */
    }

  ```

  * The `.panel-wrapper legend` selector styles the legend element within the panel, making the title stand out visually.


1. Targeting Individual Fields within the Panel:  

  ```CSS

  /* Target all form field wrappers within a panel */
  main .form form .panel-wrapper .{Type}-wrapper {
    /* Add your styles here (e.g., margin) */
    margin-bottom: 10px;
  }


  ```

  * The `.panel-wrapper .{Type}-wrapper` selector targets all wrappers with the `.{Type}-wrapper` class within the panel, allowing you to style the spacing between form fields.

1. Targeting Specific Fields (Optional):

  ```CSS

    /* Target the username field wrapper */
    main .form form .panel-wrapper .text-wrapper.field-username {
      /* Add your styles here (specific to username field) */
    }

    /* Target the password field wrapper */
    main .form form .panel-wrapper .password-wrapper.field-password {
      /* Add your styles here (specific to password field) */
    }

  ```

  * These optional selectors allow you to target specific field wrappers within the panel for unique styling, such as highlighting the username field.

+++

### Repeatable Panel

+++ HTML Structure of a Repeatable Panel

```HTML

<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
</fieldset>



```

**Example HTML Structure**

```HTML
<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-1" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-1" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-1" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>

<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-2" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-2" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-2" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>
```

Each panel has the same structure as the single panel example, with additional attributes:

* data-repeatable="true": This attribute indicates that the panel can be repeated dynamically using JavaScript or a framework.

* Unique IDs and names: Each element within the panel has a unique ID (for example, name-1, email-1) and name attribute based on the index of the panel (for example, name="contacts[0].name"). This allows for proper data collection when multiple panels are submitted.

+++ 

+++ CSS Selectors for a Repeatable Panel

* Targeting All Repeatable Panels:

```CSS

  /* Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }


```

The selector styles all panels that can be repeated, ensuring a consistent look and feel.


* Targeting Individual Fields within a Panel:

```CSS

/* Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}

```
This selector styles all field wrappers within a repeatable panel, maintaining consistent spacing between fields.

* Targeting Specific Fields (within a Panel):

```CSS
/* Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all



```

+++

### File attachment

+++ HTML Structure for File Attachment

```HTML

<div class="file-wrapper field-{FileName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false"> File Attachment </legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
    <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      <button class="file-description-remove" type="button"></button>
    </div>
  </div>
</div>


```

**Example HTML Structure**


```HTML

<div class="file-wrapper field-claim_form field-wrapper">
  <legend for="claim_form" class="field-label" data-visible="false">File Attachment</legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
  </div>
  <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="claim_form"
         name="claim_form" autocomplete="off" multiple="" required="required" data-max-file-size="2MB">
  <div class="files-list">
    </div>
</div>

```

* The class attribute uses the provided name for the file attachment (claim_form).
* The id and name attributes of the input element match the file attachment name (claim_form).
* The files-list section is initially empty. It is populated dynamically with JavaScript when files are uploaded.

+++ 

+++ CSS Selectors for the File Attachment component

* Targeting the Entire File Attachment Component:

```CSS

/* Target the entire file attachment component */
main .form form .file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}


```

This selector styles the entire file attachment component, including the legend, drag area, input field, and list.

* Targeting Specific Elements:

```CSS

/* Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}


```

These selectors allow you to style various parts of the file attachment component individually. You can adjust the styles to match your design preferences.

+++


## Styling components

You can style form fields based on their specific type (`{Type}-wrapper`) or individual names (`field-{Name}`). This allows for more granular control and customization of your form's appearance.

### Styling Based on Field Type

You can use CSS Selectors to target specific field types and apply styles consistently. 

+++ HTML Structure

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>

```

**Example HTML Structure**

```HTML

<div class="text-wrapper field-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>


```

* Each field is wrapped in a `div` element with several classes:
   * `{Type}-wrapper`: Identifies the type of field. For example, `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `field-{Name}`: Identifies the field by its name. For example `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: A generic class for all field wrappers.
* The `data-required` attribute indicates whether the field is required or optional.
* Each field has a corresponding label, input element, and potential additional elements like placeholders and descriptions.


+++ 


+++ Example CSS Selectors

```CSS

/* Target all text input fields */
main .form form .text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
main .form form .number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}


```

+++

### Styling Based on Field name

You can also target individual fields by name to apply unique styles. 

+++ HTML Structure

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>

```

**Example HTML Structure**

```HTML

<div class="number-wrapper field-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>


```

+++ 

+++ Example CSS Selector

```CSS

main .form form .field-otp input {
   letter-spacing: 2px
}


```

This CSS targets all input elements that are located within an element that has the class `field-otp`. Your form's HTML structure follows conventions of the Adaptive Forms Block, this implies there's a container marked with the class "field-otp" holds the field with the name "otp".

+++ 




## See also

{{universal-editor-see-also}}
