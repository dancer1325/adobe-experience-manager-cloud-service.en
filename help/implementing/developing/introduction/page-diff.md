---
title: Developing and Page Diff
description: Understand how the Page Diff feature works and how it can impact a developer
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
feature: Developing
role: Admin, Architect, Developer
---
# Developing and Page Diff {#developing-and-page-diff}

## Feature Overview {#feature-overview}

Content creation is an iterative process. Authoring with efficiency requires being able to see what has changed from one iteration to another. Viewing one page version and then the other is inefficient and prone to error. An author wants to be able to compare the current page to a previous version side-by-side with the differences highlighted.

The page diff allows a user to compare the current page to launches, previous versions, and so on. For details of this user feature, see [Page Diff](/help/sites-cloud/authoring/sites-console/page-diff.md).

## Operation Details {#operation-details}

When comparing versions of a page, the previous version that the user wants to compare is recreated by AEM in the background to facilitate the diff. This previous version is necessary to render the content [for side-by-side comparison](/help/sites-cloud/authoring/sites-console/page-diff.md).

This recreation operation is done by AEM internally and is transparent to the user and requires no intervention. However, an administrator viewing the repository, for example, in CRXDE Lite, would see these recreated versions within the content structure.

When content is compared, the whole tree up to the page to compare is recreated in the following location:

`/tmp/versionhistory/`

A cleanup task runs automatically to clean up this temporary content.

## Limitations {#limitations}

The diff occurs client-side by way of DOM comparison, making the diff process simple. However, there are several limitations that must be considered by the developer.

* This feature uses CSS classes that are not namespaced to the AEM Product. If other custom CSS classes or third-party CSS classes with the same names are included on the page, the display of the diff may be affected.

  * `html-added`
  * `html-removed`
  * `cq-component-added`
  * `cq-component-removed`
  * `cq-component-moved`
  * `cq-component-changed`

* Because the diff is client-side and runs on page load, any adjustments to the DOM after the client-side diff service has run are not accounted for. This process may affect the following:

  * Components that use AJAX to include content
  * Single Page Applications
  * JavaScript based components that manipulate the DOM upon user interaction.
