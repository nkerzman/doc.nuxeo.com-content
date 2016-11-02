---
title: Bootstrap Your Case Management Project
review:
    comment: ''
    date: ''
    status: ok
toc: true
confluence:
    ajs-parent-page-id: '22380617'
    ajs-parent-page-title: Quick Start Series
    ajs-space-key: NXDOC60
    ajs-space-name: Nuxeo Platform Developer Documentation — 6.0
    canonical: Bootstrap+Your+Case+Management+Project
    canonical_source: >-
        https://doc.nuxeo.com/display/NXDOC60/Bootstrap+Your+Case+Management+Project
    page_id: '22380764'
    shortlink: 3IBVAQ
    shortlink_source: 'https://doc.nuxeo.com/x/3IBVAQ'
    source_link: /display/NXDOC60/Bootstrap+Your+Case+Management+Project
tree_item_index: 200
history:
    -
        author: Solen Guitter
        date: '2015-07-16 08:32'
        message: ''
        version: '10'
    -
        author: Manon Lumeau
        date: '2014-09-16 15:50'
        message: ''
        version: '9'
    -
        author: Manon Lumeau
        date: '2014-07-21 11:27'
        message: ''
        version: '8'
    -
        author: Solen Guitter
        date: '2014-07-18 10:50'
        message: ''
        version: '7'
    -
        author: Solen Guitter
        date: '2014-07-18 10:48'
        message: formatting
        version: '6'
    -
        author: Alain Escaffre
        date: '2014-05-04 00:44'
        message: ''
        version: '5'
    -
        author: Alain Escaffre
        date: '2013-10-29 14:09'
        message: ''
        version: '4'
    -
        author: Alain Escaffre
        date: '2013-10-29 14:03'
        message: ''
        version: '3'
    -
        author: Alain Escaffre
        date: '2013-10-29 13:30'
        message: ''
        version: '2'
    -
        author: Alain Escaffre
        date: '2013-10-29 13:18'
        message: ''
        version: '1'

---
{{! excerpt}}

The Nuxeo Platform is a perfect choice for implementing a case management project. The platform provides all the necessary elements: strong information typing, rich form management, structure and document templating tools, event bus for plugging custom rules, powerful workflow engine, content lists and queues mechanisms. Nuxeo Studio allows semi-technical people to inject business requirements in the application while powerful API and great Java framework provide practically no limit in integrating with external applications or adding custom features.

{{! /excerpt}}

Let's go through the important steps when implementing a case management project.

## Defining Your Case Model

1.  From Nuxeo Studio, design your data model and structure, using document type, schemas and content-template features. A case has a specific type, and specific substructure.&nbsp;
    ![]({{file name='case-default-structure.png'}} ?w=200,border=true,thumbnail=true)
2.  Also define a default form for your case and the sub documents. At the beginning, just consider filling all the information at once. You will refine later the various forms and views you need depending on the role of the user.
    ![]({{file name='case-default-form.png'}} ?w=500,border=true)
3.  If you have some data that should come from remote systems, you should define your integration mode:
    *   Store a foreign key on the case and display the information by doing live queries;
    *   Fetch the data at creation of your case, and provide a way to synchronize it all the way long.

## Defining the Case Life Cycle

1.  Define a base life cycle for your case and implement it using the [life cycle editor in Studio]({{page space='studio' page='life-cycle'}}).
    ![]({{file name='case-lifecycle.png'}} ?w=600,border=true)
2.  List the roles of your case management project, make the analysis of who should work when on your case and on which data. Each main phase of your case processing may be the object of a dedicated workflow model design. Or a simple task. You must define how you want to orchestrate all of the phases:
    *   Either by a global workflow that may be call subworkflows
        ![]({{file name='Sub-Workflow orchestration.png'}} ?w=400,border=true)
    *   or, in a more adaptive style, launching small workflows depending on some pre-defined event-based conditions (click on a given button, change of state of the case, &hellip;). You may also want to integrate Nuxeo with an external rules engine that would provide even more induction capabilities.

## Refining Your Users Views

Now that you start having a pretty good idea of which user should fill which information, you can refine the user experience:

*   By spreading all your business data among different tabs for making them simpler, and by organizing the main case view in a nice way. You can use for this the forms and content views features, as well as the tab designer feature, in Studio.
    ![]({{file name='tabular-form.png'}} ?w=600,border=true) ![]({{file name='incident-valuation.png'}} ?w=600,border=true)
*   By providing working queues, that help organize the case worker job. A working queue is a mechanism for displaying cases depending on some of their criteria (nature, life cycle, customer id, ...)
    ![]({{file name='cases-queues.png'}} ?w=600,border=true)
*   By using the [Shared bookmark plugin](https://github.com/nuxeo/nuxeo-platform-classification), that helps users sorting by themselves the cases.

## Adding Automation on Content Processing

It is very frequent in case management projects that the systems generates automatically some documents using the data that was already stored in the system. You may want to use [the template rendering module]({{page space='userdoc60' page='template-rendering-addon'}}) for generating professional-class documents, either in Office format or PDF, that you can then send via emails or distribute to external partners via FTP or using a dedicated folder in the system, etc.

## Reporting

Case management applications are very strategical for managers as they are most of the time at the heart of the activity of the department. Thus it is a great source for tracking potential optimizations regarding internal process. Computing some mindful statistics around tasks closing, case life length, etc. may be very meaningful. You can use our [Birt Report integration module ]({{page space='userdoc60' page='nuxeo-birt-integration'}})for this, or any external BI tool.