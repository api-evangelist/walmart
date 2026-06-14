# Walmart GraphQL Schema

## Overview

This conceptual GraphQL schema represents the Walmart Marketplace API surface, covering the full lifecycle of retail commerce operations available through the [Walmart Developer Portal](https://developer.walmart.com/). The schema is derived from the REST APIs offered across Walmart Marketplace, Dropship Vendor (DSV), and Walmart Fulfillment Services (WFS) programs.

Walmart does not currently publish a public GraphQL endpoint. This schema is a conceptual mapping of Walmart's REST API capabilities into GraphQL types, intended for integration planning, tooling, and API literacy purposes.

## Source APIs

- Walmart Marketplace Feeds API — https://developer.walmart.com/api/us/mp/feeds
- Walmart Marketplace Items API — https://developer.walmart.com/api/us/mp/items
- Walmart Marketplace Prices API — https://developer.walmart.com/api/us/mp/price
- Walmart Promotions API — https://developer.walmart.com/api/us/mp/promotion
- Walmart Orders API — https://developer.walmart.com/api/us/mp/orders
- Walmart Returns API — https://developer.walmart.com/api/us/mp/returns
- Walmart Inventory API — https://developer.walmart.com/api/us/mp/inventory
- Walmart Marketplace Fulfillment API — https://developer.walmart.com/doc/us/mp/us-mp-fulfillment/
- Walmart Marketplace Insights API — https://developer.walmart.com/doc/us/mp/us-mp-insights/
- Walmart Marketplace Notifications API — https://developer.walmart.com/doc/us/mp/us-mp-notifications/
- Walmart Marketplace Reports API — https://developer.walmart.com/doc/us/mp/us-mp-onrequestreports/
- Walmart Marketplace Settings API — https://developer.walmart.com/doc/us/mp/us-mp-settings/
- Walmart Marketplace Shipping API — https://developer.walmart.com/doc/us/mp/us-mp-sww/
- Walmart Marketplace Authentication API — https://developer.walmart.com/api/us/supplier/auth
- Walmart Dropship Vendor Costs API — https://developer.walmart.com/doc/us/us-supplier/us-supplier-cost/
- Walmart Dropship Vendor Inventory API — https://developer.walmart.com/doc/us/us-supplier/us-supplier-inventory/
- Walmart Dropship Vendor Orders API — https://developer.walmart.com/doc/us/us-supplier/us-supplier-orders/
- Walmart Dropship Vendor Lag Time API — https://developer.walmart.com/doc/us/us-supplier/us-supplier-lagtime/

## Schema Design

The schema is organized around the following capability domains:

### Item Management
Types covering item setup, catalog management, taxonomy, and media. Walmart's item setup requires detailed product specifications, condition, shipping weight, and category assignment. Bulk item management uses feed-based uploads.

Key types: `Item`, `WalmartItem`, `Product`, `ItemDescription`, `ItemImage`, `ItemMedia`, `ItemCategory`, `ItemSubcategory`, `ItemSpec`, `ShippingWeight`, `ItemCondition`, `ItemStatus`, `StoreCatalog`, `BulkUpload`, `FeedStatus`

### Pricing and Promotions
Types for retail price, sale price, was-price, comparison price, and promotional pricing events including rollbacks, coupons, and special buys. The Repricer capability allows rules-based competitive pricing.

Key types: `Price`, `WalmartPrice`, `RetailPrice`, `SalePrice`, `WasPrice`, `ComparisonPrice`, `PromotionalPrice`, `Promotion`, `Coupon`, `Rollback`, `SpecialBuy`

### Offers and Fulfillment
Types covering seller offers, fulfillment method selection (seller-fulfilled, WFS, DSV), shipping options, pickup windows, and delivery eligibility.

Key types: `Offer`, `SellerOffer`, `FulfillmentType`, `ShippingOption`, `PickupTimes`, `DeliveryEligible`

### Order Management
Types for purchase orders, order lines, order status lifecycle, shipment tracking, and acknowledgment flows. Orders can be fulfilled by marketplace sellers, WFS, or DSV suppliers.

Key types: `Order`, `WalmartOrder`, `OrderLine`, `OrderLineStatus`, `Shipment`, `ShipmentCarrier`, `TrackingInfo`

### Returns and Refunds
Types for customer-initiated returns from Walmart.com, covering return lines, refund amounts, and refund status. Special handling exists for HAZMAT, freight, and other exception categories.

Key types: `ReturnOrder`, `ReturnLine`, `RefundAmount`, `RefundStatus`

### Inventory
Types for item inventory levels at ship nodes (fulfillment centers), inventory updates in bulk, and location-specific inventory queries. Applies to both Marketplace sellers and DSV suppliers.

Key types: `Inventory`, `InventoryLevel`, `InventoryUpdate`, `LocationInventory`

### Marketplace and Seller
Types for marketplace identity, seller profiles, seller performance metrics, and the pro seller badge program. Insights types enable discovery of trending items and listing quality scores.

Key types: `Marketplace`, `Seller`, `SellerInfo`, `SellerPerformance`, `WalmartPlus`

### Customer
Types representing customer order history, contact details, and shipping addresses as surfaced through order management APIs.

Key types: `Customer`, `CustomerOrder`, `CustomerAddress`, `CustomerContact`

### Authentication and Access
Types for OAuth 2.0 token-based authentication used across all Walmart Marketplace and DSV APIs. Tokens are short-lived and scoped to a consumer ID and private key pair.

Key types: `APIKey`, `Authentication`, `Token`

### Notifications and Webhooks
Types for webhook subscription management, event types, and notification payloads. Events include order creation, inventory depletion, item unpublishing, and more.

Key types: `Webhook`

### Reports
Types for on-request and pre-generated item and payment reports, report status polling, and download URL retrieval.

Key types: `Report`, `ReportType`

## Access Model

Walmart API access is gated:
- Marketplace APIs require approved Marketplace seller status
- DSV APIs require an active drop ship vendor supplier relationship
- WFS APIs require enrollment in the Walmart Fulfillment Services program
- All APIs use OAuth 2.0 with consumer ID and private key credentials
- A sandbox environment is available at https://developer.walmart.com/doc/sandbox/

## References

- Developer Portal: https://developer.walmart.com/
- GitHub Organization: https://github.com/walmartlabs
- API Status: https://developer.walmart.com/apiStatus
- Terms of Service: https://developer.walmart.com/faq/terms-and-conditions
- FAQ: https://developer.walmart.com/faq/us/
- Sandbox: https://developer.walmart.com/doc/sandbox/
