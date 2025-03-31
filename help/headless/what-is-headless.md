---
title: What is a Headless CMS?
description: Learn about Headless CMS. How do they work? What are the alternatives and differences? Why would you want to use a Headless CMS?
exl-id: 53f24f69-ad49-4b8e-9a91-36cd64c1f2b9
feature: Headless
role: Admin, Developer
---
# What is a Headless CMS? {#what-is-a-headless-cms}

* Headless content management
  * use case
    * COMMON today's web design / 
      * 💡frontend, client-side applications -- is decoupled from the -- backend, content management system 💡
* headless CMS
  * responsible for
    * (backend) content management services
    * mechanisms / enable (frontend) applications -- can access -- that content

## What is a Content Management System (CMS)? {#content-management-system}

* content management system (CMS)
  * about content / -- provided by -- your online experiences
    * store,
    * manage
    * deliver  

## Traditional CMS {#traditional-cms}

* ==
  * backend functionality /
    * store content
    * deliver
  * frontend technology /
    * render the markup -- displayed by the -- browser 
* enable you
  * FULL control of the
    * content
    * formatting
* MISS
  * flexibility / needed | today's fast-moving environment
    * _Example:_ interfacing -- with -- external apps

## Headless CMS {#headless-cms}

* -> backend -- is decoupled from -- frontend  
* == content backend /
  * 's goal
    * content repository / -- accessible via an -- API
      * -> can be display | ANY device
  * requirements
    * 👀content structured -- based on a -- model or schema 👀
* frontend
  * fetches content -- , via Content Delivery API, from the -- headless backend
  * maintains formatting & layout 
  * _Example:_ React or Angular application
* enable
  * 👀reuse content -- ACROSS -- MULTIPLE channels👀 -> frontend development process 
    * MORE efficient
    * VERY code and IT-centric 

## Content Delivery APIs {#content-delivery-apis}

* headless CMS
  * -- can provide -- >=1 ways of exposing content -- to -- client-side applications
    * HTTP REST APIs,
      * _Example:_ if content matches SOME criteria -> provide JSON
      * cons
        * ⚠️NORMALLY deliver TOO MUCH content -- to a -- client application ⚠️
          * -> client -- will have to -- parse & filter out 
    * GraphQL APIs
      * 👀MORE focused mechanism / client applications -- can query for -- concrete need content 👀 

## Full-Stack CMS {#fullstack-cms}

* TODO:
A Full-Stack CMS commonly represents the traditional topology for content management and delivery, by including the content backend and frontend technology for rendering experiences. 
Content delivery in full-stack CMS commonly happens over internal content delivery API's.
The frontend functionality is typically specific to the fullstack CMS. 
This coupling of frontend technology with content backend allows for what-you-see-is-what-you-get (WYSIWYG) experience authoring as a key benefit. 

## Hybrid CMS {#hybrid-cms}

A modern evolution of the full-stack CMS can be a hybrid CMS. This aims to combine the best of both worlds:

* efficient frontend development across channels using modern frontend tools, 
* while retaining WYSIWYG experience authoring to empower non-technical users, and to avoid IT becoming a bottleneck for cross-organizational content and experience management. 

This is achieved by embracing modern frontend frameworks such as React but maintaining an essential minimum of coupling with the content backend. 

## Decoupled CMS {#decoupled-cms}

While the term decoupled CMS is sometimes used independently, it essentially describes a headless CMS backend by emphasizing its key characteristic of being decoupled from the client-side frontend application. 

## Headful CMS {#headful-cms}

This is another term for a traditional CMS.

## Further Reading {#further-reading}

You can read more about using AEM in a headless CMS topology here: 

* [Introduction to Adobe Experience Manager as a Headless CMS](/help/headless/introduction.md)
