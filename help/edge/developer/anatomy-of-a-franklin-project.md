---
description: This document describes what a typical project should look like from a code standpoint. Before reading this document, please familiarize yourself with the document Getting Started - Developer Tutorial.
title: The Anatomy of a Project
feature: Edge Delivery Services
exl-id: 7097fdda-d87f-4867-b58c-65b04be0fa96
role: Admin, Architect, Developer
---
# The Anatomy of a Project

{{$include a73ae88d-e8e4-419a-88a1-c8d3fbec4c45}}

* goal
  * project's anatomy

* buildless approach
  * == runs -- DIRECTLY from -- your GitHub repo 
    * for content preview, | https://<branch>--<repo>--<owner>.aem.page/
    * for production site, | https://<branch>--<repo>--<owner>.aem.live/
  * steps
    * install the AEM GitHub bot | your repo,

* ALL resource | your GitHub repo
  * 💡AVAILABLE | your website 💡
    * _Example:_ "/scripts/scripts.js" | your GitHub repo | main branch -> AVAILABLE | "https://main--<repo>--<owner>.aem.page/scripts/scripts.js"

## “special” files / -- used by -- Adobe Experience Manager
* allows
  * connecting the content | your website
* placed | root path

### fstab.yaml
* 👀-- connect to -- your Google Drive OR SharePoint folders / contain your content👀 
* uses
  * how the code | your GitHub repo -- gets combined with -- your content source's content
* provides a 
  * folder mapping facility / enables you
    * extensionless “routes” -- can be mapped to a -- given piece of content OR static HTML

### head.html
* MOST important extension point -- to influence the -- markup of the content 
* uses
  * injected | server side -- as part of the -- HTML `<head>` + -- combined with -- content's metadata
* recommendations
  * ❌NO change it ❌
  * ❌NO add
    * marketing technology (_Example:_ Adobe Web SDK, Google Tag Manager or other 3rd party scripts)❌ 
    * inline scripts or styles❌
* _Examples:_
  * [aem-boilerplate](https://github.com/adobe/aem-boilerplate/blob/main/head.html)
  * [express-website](https://github.com/adobe/express-website/blob/main/head.html)
  * [business-website](https://github.com/adobe/business-website/blob/main/head.html)

### 404.html
* TODO:

### TODO: