- [Introduction](#introduction)
- [B2B Commerce](#b2b-commerce)
  - [Cache](#cache)
- [B2C Commerce](#b2c-commerce)
  - [Eclipse UX Studio](#eclipse-ux-studio)
  - [MVC structure](#mvc-structure)
    - [View Layer](#view-layer)
    - [Controller Layer](#controller-layer)
    - [Data Model Layer](#data-model-layer)
  - [Storefront Reference Architecture (SFRA)](#storefront-reference-architecture-sfra)
  - [Salesforce Connector](#salesforce-connector)
  - [Open Commerce API (OCAPI)](#open-commerce-api-ocapi)
    - [OCAPI Explorer](#ocapi-explorer)
    - [Authentication](#authentication)
  - [Payments](#payments)
- [Courses](#courses)
- [Videos](#videos)
- [YouTube Channels](#youtube-channels)
- [Extensions for VS Code](#extensions-for-vs-code)

# Introduction

- What are Options for building cloud base ecommerce websites with Salesforce?
- Leading practices around designing and building ecommerce websites on Salesforce
- Application lifecycle management on Salesforce

> Salesforce bought DemandWare for B2C commerce (rebranded as SFCC Salesforce commerce cloud)

[Demandware is Now the Salesforce Commerce Cloud](https://www.salesforce.com/blog/2016/09/demandware-salesforce-commerce-cloud.html)

> Salesforce bought CloudCraze for B2B commerce (native Salesforce app, in it's own domain)

# B2B Commerce

> native app built on Salesforce platform which is installed from app exchange

![alt](assets/chrome_dbgGFyjLNm.png)

products available by customizable rules like:

- geography
- bundle

## Cache

granular options (specific) depending on the changes

> think about what you want to cache, it's better to cache everything than nothing as
> it impacts the site critically

> most of the setup can be done thru the UI (declaratively), but you can also do stuff programmatically

# B2C Commerce

![alt](assets/chrome_FYMojV12JY.png)

Point of Delivery (POD) - data centers around world, equivalent of instance in the Salesforce

Realm - equivalent of Salesforce org, within Realm multiple ecommerce sites

each ecommerce site will have:

- a Primary Instance Group (PIG)
- a Secondary Instance Group (SIG)

> Only difference between PIG and SIG is the power of the machines (storage, CPU etc.)

last there's an Infrastructure Layer (storage, network etc.)

![alt](assets/salesforce-15-v6GvG1mO6D.png)

![alt](assets/salesforce-14-ay6xLFFpvc.png))

## Eclipse UX Studio

> Visual Studio is becoming the major IDE for Salesforce development

[Install and Configure UX Studio](https://trailhead.salesforce.com/en/content/learn/modules/b2c-developer-resources-and-tools/b2c-developer-install-and-configure-ide)

> Start up Eclipse and use the "Install New Software" link under the Help menu. Paste the URL in the "Work with" entry and give it a name. The rest is dialog based and only requires accepting a license agreement.

[Install or Update UX Studio](https://documentation.b2c.commercecloud.salesforce.com/DOC1/index.jsp?topic=%2Fcom.demandware.dochelp%2FSiteDevelopment%2FInstallUXStudio.html)

> For debugging / viewing pipelines we still have to use Eclipse and demandware plugin

> Digital Development perspective in Eclipse means you installed UX Studio

![Digital Development](assets/chrome_0NxUEJ5GQH.png)

![alt](assets/chrome_rhkqM9Gvpf.png)

> API definitions are updated on the monthly basis

> Cartridge - building block of a site

Attaching the Cartridge to a Digital Server will push it to the sandbox (auto-upload of code to the sandbox).

![alt](assets/salesforce-1-GgeG5kVxoV.png)

> Merchant is responsible for content and the way the site functions - higher level

> Administration tab - useful for devs/admins, lower level, everything related to code

> SiteGenesis is a fully functioning site, it's not recommended to build your own site but use this as a starting point

> SiteGenesis is being replaced with a new architecture called Storefront Reference Architecture (SFRA)

![alt](assets/salesforce-16-RNF0x22lTr.png)

> ISML - Internet Store Markup Language

## MVC structure

### View Layer

Storefront toolkit - floats on the page, allows quick reference to utilities

![alt](assets/salesforce-2-RbT9PxdQKk.png)

> CTRL+SHIFT+R - open file

Convention based so `Product-ShowInCategory` is a `controller-action`, `Product` is the controller, `ShowInCategory` is an action.

![alt](assets/salesforce-8-tXTKqRNQGI.png)

`ISML expressions`
`pdict - pipeline dictionary`
`Local Include` - static markup dumped on the page which calls it
`Remote Include` - markup used on some other page

Cache Information shows caching info for everything on the page (use Business Manager for cache control)
![alt](assets/salesforce-9-QpOrgJ2A67.png))

### Controller Layer

> Written in JS, not in Pipelines

![alt](assets/salesforce-a-XPf9QsvfDd.png)

![alt](assets/salesforce-c-o9eg01uG95.png)

> Use Request Log from the Toolkit for debugging controllers (gives full stack overview)

![alt](assets/salesforce-b-ebDfgVPfHi.png)

Also use Commerce Cloud Digital API for reference.

![alt](assets/salesforce-d-YB5v5S1lfD.png)

> Administration tab > Pipeline Profiler (shows the name Pipeline but used to debug the performance aspect of controllers)

![alt](assets/salesforce-e-N7a5Y4jef1.png)

Turn it off when done as it will kill your sandbox!

### Data Model Layer

Standard Objects aka System Objects (product, catalog, price)
Custom Objects (creating instance or schema)

> Go to Administration tab > Site Development > Custom Objects Types

![alt](assets/salesforce-f-DKj7kkSgox.png)

or programmatically using `CustomObjectMgr`

> Transactional data should not be stored in custom objects.

## Storefront Reference Architecture (SFRA)

Use SFRA for new sites, don't use SiteGenesis architecture.

> Moving from SiteGenesis and pipelines to SFRA needs custom implementation
> and existing connectors only provide starting point for integration.

![alt](assets/salesforce-17-52vN0rs7VV.png)

> Not using the Lighting design system

> JavaScript development - no APEX, no VisualForce

[Get the SFRA Repositories from GitHub](https://documentation.b2c.commercecloud.salesforce.com/DOC2/index.jsp?topic=%2Fcom.demandware.dochelp%2FSFRA%2FSFRASetup.html)

![alt](assets/salesforce-g-NMNiQsTy4Y.png)

[Storefront Reference Architecture](<[https://link](https://www.salesforce.com/products/commerce-cloud/resources/commerce-cloud-storefront-reference-architecture/)>)

> Commerce Cloud Storefront Reference Architecture combines best practices in site design, merchandising, and technical architecture to provide an out-of-the-box blueprint for merchants to build sites as unique as their brands.

## Salesforce Connector

> Sync data between Commerce Cloud and Service Cloud or Marketing Cloud etc..

Custom implementation needed, only provides starting point for integration.

## Open Commerce API (OCAPI)

[Open Commerce API 20.4](https://documentation.b2c.commercecloud.salesforce.com/DOC3/index.jsp?topic=%2Fcom.demandware.dochelp%2FOCAPI%2Fcurrent%2Fusage%2FAPIExplorer.html)

![alt](assets/salesforce-1e-eU6f4haGVV.png)

![alt](assets/salesforce-1f-3lK7uI5NF1.png)

![alt](assets/salesforce-1g-V2AYOvKAuR.png)

![alt](assets/salesforce-1l-UrgWDDGxes.png)

- Shop APIs

> to access public shop information such as product and catalog data, images, recommendations, prices or promotions

- Data APIs

> to access or update merchant resources such as coupons, customer lists, slot configurations or content

- Meta APIs

> to access details about the resources and documents provided by the Open Commerce API

![alt](assets/salesforce-1b-EK2Qap4NpN.png)

![alt](assets/salesforce-1c-EOCkAc5a2m.png)

![alt](assets/salesforce-1d-CFkWsGm0Nj.png)

### OCAPI Explorer

[API Explorer 20.4](https://documentation.b2c.commercecloud.salesforce.com/DOC3/index.jsp?topic=%2Fcom.demandware.dochelp%2FOCAPI%2Fcurrent%2Fusage%2FAPIExplorer.html)

The API Explorer tool allows application developers to interactively explore the Open Commerce APIs in a few ways:

- Browse and review APIs.
- Test APIs by launching requests.

![alt](assets/salesforce-1h-09S2o2UU8Z.png)

### Authentication

JWT - for guest, credential, session
Oauth - Client Credentials or Business Manager login depending on the needed resources (granular permissions)

## Payments

[Salesforce Commerce Cloud Adyen Cartridge](https://www.adyen.com/partners/salesforce-commerce-cloud)
[Github - Salesforce Commerce Cloud Adyen Cartridge](https://github.com/Adyen/adyen-salesforce-commerce-cloud)

> The cartridge integrates Secured Fields for all card payments. Local/redirect payment methods are integrated with Checkout API. For Point Of Sale (POS) payments in SiteGenesis, we use Terminal API using Cloud-based communication.

[Worldpay Salesforce Commerce Cloud Cartridge](https://github.com/Worldpay/salesforce-commerce-cloud#worldpay-link-cartridge)

> Worldpay is a leading global provider of payment and risk services, processing millions of transactions every day. We provide an end-to-end service including card acquiring, treasury, gateway, alternative payments and risk management, all of which can be accessed through a single integration.

# Courses

[Pluralsight](https://www.pluralsight.com/browse/software-development/salesforce)

[Salesforce Commerce Cloud ( Demandware ) Head Start](https://www.udemy.com/course/salesforce-commerce-cloud/)

[Salesforce Commerce Cloud Development Quickstart Guide](https://www.udemy.com/course/salesforce-commerce-cloud-development-quickstart-guide/)

[Develop for Salesforce B2C Commerce](https://trailhead.salesforce.com/en/content/learn/trails/develop-for-commerce-cloud)

# Videos

[![SFCC Debug Pipeline on Eclipse](http://img.youtube.com/vi/5G5DURIINc0/0.jpg)](http://www.youtube.com/watch?v=5G5DURIINc0 'SFCC Debug Pipeline on Eclipse')

[![Demystifying Salesforce Commerce Cloud Development with Gaurav Kheterpal](http://img.youtube.com/vi/FSOaLAQl78s/0.jpg)](http://www.youtube.com/watch?v=FSOaLAQl78s 'Demystifying Salesforce Commerce Cloud Development with Gaurav Kheterpal')

[![Demystifying Mobile-First eCommerce Sites with Commerce Cloud SFRA](http://img.youtube.com/vi/23aK6B3F1TE/0.jpg)](http://www.youtube.com/watch?v=23aK6B3F1TE 'Demystifying Mobile-First eCommerce Sites with Commerce Cloud SFRA')

[![Salesforce Commerce Cloud - Introduction & Onboarding](http://img.youtube.com/vi/siuGOnOycv4/0.jpg)](http://www.youtube.com/watch?v=siuGOnOycv4 'Salesforce Commerce Cloud - Introduction & Onboarding')

[![Introduction to Commerce Cloud for Developers](http://img.youtube.com/vi/sON11osEco4/0.jpg)](http://www.youtube.com/watch?v=sON11osEco4 'Introduction to Commerce Cloud for Developers')

[![Introduction to Salesforce Commerce Cloud](http://img.youtube.com/vi/lqSUwPE1HkA/0.jpg)](http://www.youtube.com/watch?v=lqSUwPE1HkA 'Introduction to Salesforce Commerce Cloud')

[![Introduction to Commerce Cloud's Mobile-First Reference Architecture](http://img.youtube.com/vi/-Td7CwJ6zdE/0.jpg)](http://www.youtube.com/watch?v=-Td7CwJ6zdE 'Introduction to Commerce Clouds Mobile-First Reference Architecture')

[![Commerce Cloud for Salesforce Developers with Jon Jessup](http://img.youtube.com/vi/U93bgxI0LIM/0.jpg)](http://www.youtube.com/watch?v=U93bgxI0LIM 'Commerce Cloud for Salesforce Developers with Jon Jessup')

![alt](assets/salesforce-w-aWA0jkhEoE.png)

![alt](assets/salesforce-x-jAdpKPaa3j.png)

> Business Manager for customizing and merchandising the site

![alt](assets/salesforce-y-IXipKcxVEY.png)

![alt](assets/salesforce-z-e8ZgB2xkLs.png)

> Einstein is used to serve the most relevant products based on your search, cart etc.

![alt](assets/salesforce-10-66ln01QDxY.png)

> Integration between Commerce Cloud and Marketing Cloud and Service Cloud

![alt](assets/salesforce-11-n86X9QnaH7.png)

![alt](assets/salesforce-12-CIsLkobHHr.png)

![alt](assets/salesforce-13-ND2tRtDknO.png)

[![Whats New in the Commerce Cloud B2C Developer's Toolbox](http://img.youtube.com/vi/lAsXbpF8hVA/0.jpg)](http://www.youtube.com/watch?v=lAsXbpF8hVA 'Whats New in the Commerce Cloud B2C Developers Toolbox')

![alt](assets/salesforce-1i-0Ra9PKTG6s.png)

[![Demonstrating API First Commerce with Commerce Cloud's Open Commerce APIs](http://img.youtube.com/vi/tdTOSEI-P08/0.jpg)](http://www.youtube.com/watch?v=tdTOSEI-P08 'Demonstrating API First Commerce with Commerce Clouds Open Commerce APIs')

![alt](assets/salesforce-1j-2qHyt21634.png)

[Demo Video](https://youtu.be/lAsXbpF8hVA?t=1282)

# YouTube Channels

[Salesforce Developers](https://www.youtube.com/user/DeveloperForce/videos)

[Bay Area Salesforce Developer Group](https://www.youtube.com/channel/UCdTNaauk7anhmVfg-ulzX2Q/videos)

# Extensions for VS Code

[Salesforce Extensions for Visual Studio Code](https://developer.salesforce.com/tools/vscode/)
[Salesforce Extension Pack](https://marketplace.visualstudio.com/items?itemName=salesforce.salesforcedx-vscode)

[Visual Studio Code integration with Demandware A.K.A Salesforce Commerce Cloud](https://medium.com/@manusaini0088/visual-studio-code-integration-with-demandware-aka-salesforce-commerce-cloud-b2c2ff49e22b)

[Prophet Debugger](https://marketplace.visualstudio.com/items?itemName=SqrTT.prophet)

> A VS Code extension to work with Demandware/Salesforce Cloud code on Sandbox that support the Script Debugger API (SDAPI) 2.0
