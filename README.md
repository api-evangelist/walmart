# Walmart (walmart)
Walmart is a multinational retail corporation that operates a chain of hypermarkets, discount department stores, and grocery stores. The company is known for offering a wide range of products at competitive prices, attracting customers from all walks of life. Walmart also provides various convenience services, such as pharmacy, optical, and financial services, making it a one-stop shop for many consumers. Additionally, Walmart has a strong presence in e-commerce, offering online shopping and home delivery options. Overall, Walmart strives to provide affordable, convenient, and quality products to its customers around the world.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-search/commerce/main/_apis/walmart/apis.md)

## Scope

- **Type:** Contract 
- **Position:** Consuming 
- **Access:** 3rd-Party 

## Tags:

 - Commerce, Retail

## Timestamps

- **Created:** 2023/11/15 
- **Modified:** 2025-01-04 

## APIs

### Walmart Marketplace Feeds API
Feeds are constructed to handle bulk functions. A feed consists of an HTTP request with an attached file. The attached file contains the XML representing the objects that need to be created or updated. The Walmart APIs version 3.0 supports only Item and Feed types. Refer to the bulk endpoints in each section to see example Feeds for each feed type. Once you upload the Feeds, you can use the Feed ID to track the status of the feeds and the status of the item within those Feeds.

**Human URL:** [https://developer.walmart.com/api/us/mp/feeds](https://developer.walmart.com/api/us/mp/feeds)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Feeds, Statuses, Items, Status, Errors, Reports

#### Properties

- [Documentation](https://developer.walmart.com/api/us/mp/feeds)
- [OpenAPI](openapi/walmart-marketplace-feeds-openapi-original.yml)
### Walmart Marketplace Items API
The Item Management APIs enable you to set up and manage items on Walmart.com. Once you have completed Registration and have access to your Consumer ID and Private Key, you can get started with the integration process

**Human URL:** [https://developer.walmart.com/api/us/mp/items](https://developer.walmart.com/api/us/mp/items)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Catalog, Items, Search, Associations, (Multiple), Bulk, Feeds, Setup, Walmart, Taxonomy, Count, Groups, Status, Retire, Sku

#### Properties

- [OpenAPI](openapi/walmart-marketplace-items-openapi-original.yml)
- [Documentation](https://developer.walmart.com/api/us/mp/items)
### Walmart Marketplace Prices API
The price is a fundamental building block for your listing on Walmart.com. You can use the price management APIs to set up and manage the price for a given item

**Human URL:** [https://developer.walmart.com/api/us/mp/price](https://developer.walmart.com/api/us/mp/price)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Collections, Repricer, Strategies, Incentive, Items, Assign, Prices, Assign/Unassign, Feeds, To/from, (Multiple), Bulk, CAP, Cppreference, SKU, Sets, Up

#### Properties

- [Documentation](https://developer.walmart.com/api/us/mp/price)
- [OpenAPI](openapi/walmart-marketplace-prices-openapi-original.yml)
### Walmart Promotions API
Sellers can set regular or promotional prices for their items. Setting the Promotional prices is an option to create unique pricing for events such as clearance sales or to call out a comparison price

**Human URL:** [https://developer.walmart.com/api/us/mp/promotion](https://developer.walmart.com/api/us/mp/promotion)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Prices, Promotional, Bulk, Feeds, Promo, Sku

#### Properties

- [Documentation](https://developer.walmart.com/api/us/mp/promotion)
- [OpenAPI](openapi/walmart-marketplace-promotions-openapi-original.yml)
### Walmart Orders API
The Walmart Order Management APIs help Sellers to manage customer's Sales Orders and to stay up-to-date on orders fulfillment, which orders to fulfill, and when to fulfill them.

**Human URL:** [https://developer.walmart.com/api/us/mp/orders](https://developer.walmart.com/api/us/mp/orders)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Lines, Orders, Purchase, Ship, Shipping, Refunds, Cancel, Acknowledge, Released

#### Properties

- [Documentation](https://developer.walmart.com/api/us/mp/orders)
- [OpenAPI](openapi/walmart-marketplace-orders-openapi-original.yml)
### Walmart Returns API
Buyers can now Initiate Returns from Walmart.com for Marketplace seller items (Except for HAZMAT, OTHER or FREIGHT items). For item in the exception categories: HAZMAT or OTHER, sellers need to generate the return shipping label, and upload the label. For detailed instructions, and to download the Returns API JSON schema, see Returns guide.

**Human URL:** [https://developer.walmart.com/api/us/mp/returns](https://developer.walmart.com/api/us/mp/returns)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Issues, Orders, Refunds, Returns, Feeds, Items, Overrides

#### Properties

- [Documentation](https://developer.walmart.com/api/us/mp/returns)
- [OpenAPI](openapi/walmart-marketplace-returns-openapi-original.yml)
### Walmart Inventory API
Maintaining up-to-date inventory for your items on Walmart.com ensures a great experience for your customers and greater sales opportunities for you.

**Human URL:** [https://developer.walmart.com/api/us/mp/inventory](https://developer.walmart.com/api/us/mp/inventory)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Inventory, Inventories, Items, Nodes, Ship, Single, Sku, Bulk, Feeds, Multiple, Fulfillment, WFS

#### Properties

- [Documentation](https://developer.walmart.com/api/us/mp/inventory)
- [OpenAPI](openapi/walmart-marketplace-inventory-openapi-original.yml)
### Walmart Dropship Vendor Costs API
Drop ship vendor (DSV) suppliers can update the cost for a single item or multiple items in bulk with the Cost API.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-cost/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-cost/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Bulk, Cost, Feeds, Items

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-cost/)
- [OpenAPI](openapi/walmart-dropship-vendor-costs-openapi-original.yml)
### Walmart Dropship Vendor Inventory API
Walmart's Inventory Management API provide drop ship vending (DSV) suppliers with mechanisms to update and view current item inventory levels at each ship node, also known as fulfillment centers. Suppliers assign each item they fulfill drop ship vending (DSV) through one or more ship nodes. Suppliers must accurately maintain the item's inventory level at each ship node to ensure availability for customer orders.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-inventory/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-inventory/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Count, Inventory, Items, Nodes, Ship, Single, Bulk, Feeds, Inventories, Specific

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-inventory/)
- [OpenAPI](openapi/walmart-dropship-vendor-inventory-openapi-original.yml)
### Walmart Dropship Vendor Items API
The Walmart Order Management API help 1P suppliers stay up to date on order fulfillment.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Bulk, Feeds, Items, Maintain, Media, Rich, (v4), Products, Single, (v3), Sku, Expose, Taxonomy, Types

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/)
- [OpenAPI](openapi/walmart-dropship-vendor-items-openapi-original.yml)
### Walmart Dropship Vendor Lag Time API
Drop ship vending (DSV) suppliers are expected to ship items the day they receive the purchase order (PO). However, there may be times when drop ship vendors (DSV) have an item that does not ship the same day. This delay is called a lag time. These Lag Time requests allow suppliers to update the lag time or to view the number of days between when an item is ordered and when it is shipped.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-lagtime/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-lagtime/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Bulk, Feeds, Items, Lag, Time, Based, ID, Lagtime, Products, Single

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-lagtime/)
- [OpenAPI](openapi/walmart-dropship-vendor-lag-time-openapi-original.yml)
### Walmart Dropship Vendor On-Request Reports API
The On Request Reports API lets users request item reports. Request a report at any time, subscribe to notifications when the report is ready, and download the requested report.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-onrequestreports/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-onrequestreports/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Reports, Details, Single, Download, URL

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-onrequestreports/)
- [OpenAPI](openapi/walmart-dropship-vendor-on-request-reports-openapi-original.yml)
### Walmart Dropship Vendor Orders API
The Walmart Order Management API help 1P suppliers stay up to date on order fulfillment.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Lines, More, Orders, Purchase, Ship, Shipping, Cancel, Acknowledge, Single, Released

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/)
- [OpenAPI](openapi/walmart-dropship-vendor-orders-openapi-original.yml)
### Walmart Dropship Vendor Orders API
The Walmart Order Management API help 1P suppliers stay up to date on order fulfillment.

**Human URL:** [https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/](https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Generate, Items, Reports

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/)
- [OpenAPI](openapiwalmart-dropship-vendor-pre-generated-reports-openapi-original.yml)
### Walmart Marketplace Authentication API
Authentication creates and manages access tokens to ensure users are verified. The Walmart 1P Supplier APIs use open authorization (OAuth 2.0) for token-based authentication.

**Human URL:** [https://developer.walmart.com/api/us/supplier/auth](https://developer.walmart.com/api/us/supplier/auth)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Tokens, Detail

#### Properties

- [Documentation](https://developer.walmart.com/api/us/supplier/auth)
- [OpenAPI](openapi/walmart-marketplace-authentication-openapi-original.yml)
### Walmart Marketplace Fulfillment API
The Walmarts Multichannel Solution is an extension of Walmart Fulfillment Services (WFS), uniquely placed to ensure quality, scale, and efficiency for a seller to grow a successful business. The entire assortment of inventory, supply chain management and fulfillment capabilities are centralized and managed by Walmart while seller's items can be listed and sold at multiple online platforms and storefronts.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-fulfillment/](https://developer.walmart.com/doc/us/mp/us-mp-fulfillment/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Fulfillment, Quantities, Shipment, Hazmat, Hold, Items, Onhold, Search, Tracking, Inbound, Labels, Customers, Fulfillments, Orders, Deliveries, Details, Fetch, Options, Promise, Cancel, Shipments, Previews, Carrier, Quotes, Rates, Confirm, Print, Convert, Feeds, WFS, Health, Inventory, Reports, Wfs, Status, (deprecated), Logs, Errors

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-fulfillment/)
- [OpenAPI](openapi/walmart-marketplace-fulfillment-openapi-original.yml)
### Walmart Marketplace Insights API
To grow your business, you can use Insights API to learn actionable information critical to building your business and catalog offerings. With the Insights API you can learn actionable information about your current listings: Top trending items, unpublished items, and quality of item listings.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-insights/](https://developer.walmart.com/doc/us/mp/us-mp-insights/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Details, Insights, Items, Listings, Quality, Badge, Pro, Prosellerbadge, Seller, Status, Unpublished, Counts, Top, Trending, Scores, Count, Issues

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-insights/)
- [OpenAPI](openapi/walmart-marketplace-insights-openapi-original.yml)
### Walmart Marketplace Lag Time API
Lag Time is the number of days between the date an item is ordered and when it is shipped. During Item Setup, Lag Time can be set to 0 days or 1 day. Any other value used will be defaulted to 1 day.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-lagtime/](https://developer.walmart.com/doc/us/mp/us-mp-lagtime/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Feeds, Lag, Time, Lagtime

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-lagtime/)
- [OpenAPI](openapi/walmart-marketplace-lag-time-openapi-original.yml)
### Walmart Marketplace Notifications API
Push notifications or Web Hooks trigger alerts to seller applications when specific events occur, such as an item is unpublished, a new purchase order is created, an item's inventory is out of stock, etc. Whenever the trigger event occurs, Walmart will send a notification payload with event details to the seller-defined destination URL. Web Hooks help to optimize integration, automate workflows and reduce the number of times your application has to poll Walmart APIs within the throttle limits to determine if an event has occurred.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-notifications/](https://developer.walmart.com/doc/us/mp/us-mp-notifications/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Notifications, Tests, Webhooks, Subscriptions, Events, Types

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-notifications/)
- [OpenAPI](openapi/walmart-marketplace-notifications-openapi-original.yml)
### Walmart Marketplace On-Request Reports API
The On-request Reports API enables you to request item reports immediately about your items for faster retrieval. Now you can request a report at any time, subscribe to notifications that report is ready, and then you can download it.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/](https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Reports, Status, Download, URL

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/)
- [OpenAPI](openapi/walmart-marketplace-on-request-reports-openapi-original.yml)
### Walmart Marketplace Recommendations API
Assortment recommendations empower sellers understand and identify the customer demand in Walmart & market by curating personalised seller recommendations by leveraging demand signals such as Internal and external search, Best Sellers, Trending items, and more.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-assortmentrecommendations/](https://developer.walmart.com/doc/us/mp/us-mp-assortmentrecommendations/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Assortment, Growth, Recommendations, Categorization, Counts, Reject, Rejections

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-assortmentrecommendations/)
- [OpenAPI](openapi/walmart-marketplace-recommendations-openapi-original.yml)
### Walmart Marketplace Reports API
The On-request Reports API enables you to request item reports immediately about your items for faster retrieval. Now you can request a report at any time, subscribe to notifications that report is ready, and then you can download it.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/](https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Available, Dates, Files, JSON, Payments, Performance, Recon, Reports, Statements, Versions

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/)
- [OpenAPI](openapi/walmart-marketplace-reports-openapi-original.yml)
### Walmart Marketplace Reviews API
Use the Review Accelerator Program (RAP) APIs to increase the number of reviews for items with less than fifteen reviews.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-reviews/](https://developer.walmart.com/doc/us/mp/us-mp-reviews/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Accelerators, Bulk, Growth, Items, Reviews, Status, Post Purchase, RAP, Categories

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-reviews/)
- [OpenAPI](openapi/walmart-marketplace-reviews-openapi-original.yml)
### Walmart Marketplace Rules API
Walmart is making program enhancements to the existing free 2-Day Shipping Program, to enable US marketplace sellers to add multiple fulfillment centers along with capability to manage them and easily configure item assortment setup for 2-Day program. The capability, Item assortment rules for 2-Day program setup, will part of the enhancements:

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-rules/](https://developer.walmart.com/doc/us/mp/us-mp-rules/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Inactivate, Rules, Exceptions, Override, Assortment, Change, Types, Activate, Actions, Area, Shipping, Status, Results, Simulationcount, Simulations, Download, Sub Categories, Subcategories, Downloadexceptions, Areas

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-rules/)
- [OpenAPI](openapi/walmart-marketplace-rules-openapi-original.yml)
### Walmart Marketplace Settings API
The Settings API allows you to configure shipping delivery and fulfillment settings. You can create shipping templates to specify the precise delivery speed for your items. You can specify fulfillment center choices for your items. 

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-settings/](https://developer.walmart.com/doc/us/mp/us-mp-settings/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Details, Settings, Shipping, Templates, Centers, Fulfillment, Shipnodes, Center, Accounts, Levels, 3plshipnodes, Associations, Party, Configurations, Shippingprofile, Activation, Status, Coverage, Carrier, Carriers, Methods, 3plprov, Ers, Providers, Partnerprofile, Partners

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-settings/)
- [OpenAPI](openapi/walmart-marketplace-settings-openapi-original.yml)
### Walmart Marketplace Shipping API
The Ship With Walmart for US API enables walmart.com sellers to buy shipping at competitively discounted rates directly from Walmart to ship their goods to US customers.  

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-sww/](https://developer.walmart.com/doc/us/mp/us-mp-sww/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Labels, Shipping, Estimates, Detail, Orders, Purchase, Carriers, Supported, Carrier, Download, Names, Tracking, Trackings, Discard, Commercial, Invoices, Packages, Types

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-sww/)
- [OpenAPI](openapi/walmart-marketplace-shipping-openapi-original.yml)
### Walmart Marketplace Utilities API
The Utility APIs allow you to search for all Walmart item departments, all categories within a department, or retrieve the taxonomy of categories per Feed type.

**Human URL:** [https://developer.walmart.com/doc/us/mp/us-mp-utilities/](https://developer.walmart.com/doc/us/mp/us-mp-utilities/)

**Base URL:** [https://api.example.com](https://api.example.com)


#### Tags:

 - Taxonomy, Utilities, Departments, Categories, Department, Platforms, Status

#### Properties

- [Documentation](https://developer.walmart.com/doc/us/mp/us-mp-utilities/)
- [OpenAPI](openapi/walmart-marketplace-utilities-openapi-original.yml)

## Common Properties

- [Portal](https://developer.walmart.com/)
- [Docs](https://developer.walmart.com/home/us-mp/)
- [Sandbox](https://developer.walmart.com/doc/sandbox/)
- [Whats New](https://developer.walmart.com/category/us/whats-new/)
- [Support](https://developer.walmart.com/home/help/)
- [FAQ](https://developer.walmart.com/faq/us/)
- [Status](https://developer.walmart.com/apiStatus)
- [Terms of Service](https://developer.walmart.com/faq/terms-and-conditions)

## Maintainers

**FN:** API Evangelist

**Email:** info@apievangelist.com

