---
title: Using Tags
description: Tags are a quick and easy method of classifying content within a website
exl-id: d2a9f578-fe0a-48ea-851c-2c84463661e0
solution: Experience Manager Sites
feature: Authoring
role: User
---
# Using Tags {#using-tags}

Tags are a quick and easy method of classifying content within a website. Tags may be thought of as keywords or labels that can be attached to a page, an asset, or other content to enable searches to find that content and related content.

* See [Administering Tags](/help/sites-cloud/administering/tags.md) for information about creating and managing tags, and to which content tags have been applied.
* See [Tagging for Developers](/help/implementing/developing/introduction/tagging-framework.md) for information about the tagging framework and including and extending tags in custom applications.

## Ten Reasons to Use Tagging {#ten-reasons-to-use-tagging}

1. **Organizing Content** - Tagging makes life easier for authors as they can quickly organize content with little effort.
1. **Organizing Tags** - While tags organize content, hierarchical taxonomies/namespaces organize tags.
1. **Deeply Organized Tags** - With the ability to create tags and sub-tags it becomes possible to express entire taxonomic systems, covering terms, subterms and their relationships. This allows creation of a second (or third) content hierarchy in parallel to the official one.
1. **Controlled Tagging** - Tagging can be controlled by applying permissions to tags and/or namespaces to control tag creation and application.
1. **Flexible Tagging** - Tags have many names and faces: tags, taxonomy terms, categories, labels and many more. They are flexible in their content model and in the way they can be used; for instance, when outlining target demographics, categorizing and rating content or to create a secondary content hierarchy.
1. **Improved Searching** - The default search component in AEM broadly includes created tags and applied tags to which filters can be applied to narrow the results to those that are relevant.
1. **SEO Enabling** - Tags applied as page properties will automatically show up in the metatags of the page making it visible to search engines.
1. **Simple Sophistication** - Tags can simply be created from a word and the touch of a button. Afterwards, a title, description and unlimited labels can be added to provide more semantics to the tag.
1. **Core Consistency** - The tagging system is a core component of AEM and is used by all AEM capabilities to categorize content. Further, the tagging API is available to developers for creating tagging-enabled applications with access to the same taxonomies.
1. **Combines Structure & Flexibility** - AEM is ideal for working with structured information, due to the nesting of pages and paths. It is equally powerful when working with unstructured information, due to the built-in full-text search. Tagging combines the strengths of both structure and flexibility.

When designing the content structure for a site and the metadata schema for assets, consider the lightweight and accessible approach tagging provides.

## Applying Tags {#applying-tags}

In the author environment, authors may apply tags by accessing the page properties and entering one or more tags in the **Tags/Keywords** field.

To apply pre-defined tags, in the **Page Properties** window use the **Tags** field and the **Select Tags** window. The **Standard Tags** tab is the default namespace, which means there is no `namespace-string:` prefixed to the taxonomy. <!-- To apply [pre-defined tags](/help/sites-administering/tags.md), in the **Page Properties** window use the **Tags** field and the **Select Tags** window.-->

![Select multiple tags](/help/sites-cloud/authoring/assets/tags-select.png)

## Publishing Tags {#publishing-tags}

Similar to how you can publish and unpublish pages pages, you can perform the following on tags and namespaces:

### Activate {#activate}

* Activate individual tags.

  Just as with pages, created tags must be activated before they become available on the publish environment.

>[!NOTE]
>
>When you activate a page, a dialog automatically opens and enables you to activate un-activated tags belonging to the page.

### Deactivate {#deactivate}

* Deactivate the selected tags.
