---
name: walmart-order-fulfillment
description: Poll Walmart Marketplace for new purchase orders, acknowledge them, and post shipment tracking — the core seller order loop.
api: Walmart Orders API
generated: '2026-08-27'
method: generated
source: openapi/walmart-orders-api-openapi.yml, conventions/walmart-conventions.yml, rate-limits/walmart-rate-limits.yml
operations:
  - getAllOrders
  - getAllReleasedOrders
  - getAnOrder
  - acknowledgeOrders
  - shippingUpdates
---

# Fulfil a Walmart Marketplace order

## Before you start

- Get a token: `POST /v3/token` on `https://marketplace.walmartapis.com` with `Authorization: Basic base64(clientId:clientSecret)`
  and `grant_type=client_credentials`.
- Every call below needs three headers: `WM_SEC.ACCESS_TOKEN` (the token — **not** `Authorization: Bearer`),
  `WM_QOS.CORRELATION_ID` (a UUID you generate per request), and `WM_SVC.NAME`.
- There is **no idempotency key** on this API. If a write times out, do not blind-retry: re-read the order first.

## Steps

1. **Poll for work.** `getAllOrders` — `GET /v3/orders?createdStartDate=...`. Limit 5000/min. Use
   `getAllReleasedOrders` (`GET /v3/orders/released`, 60/min) if you only want orders released for fulfilment.
   Paginate with the `nextCursor` returned in the response; the cursor expires after 2 minutes.
2. **Read one order.** `getAnOrder` — `GET /v3/orders/{purchaseOrderId}`. Limit 5000/min. Note that `purchaseOrderId` and
   `customerOrderId` are different identifiers and are not interchangeable.
3. **Acknowledge.** `acknowledgeOrders` — `POST /v3/orders/{purchaseOrderId}/acknowledge`. Limit 60/min. Acknowledge before
   shipping; an unacknowledged order will not accept a shipment update cleanly.
4. **Ship.** `shippingUpdates` — `POST /v3/orders/{purchaseOrderId}/shipping`. Limit 60/min. Supply carrier, tracking number
   and tracking URL per order line.

## Rules that will bite you

- **A shipment notification cannot be withdrawn.** If you ship in error, the only correction is `refundOrderLines`.
- **Orders auto-cancel if not shipped within 30 days of creation.** A shipment update on an order older than 30 days returns
  `400 INVALID_REQUEST`.
- Shipping an already-shipped or already-cancelled order returns `400 INVALID_REQUEST`. Read the order status first.
- On `429 REQUEST_THRESHOLD_VIOLATED`, read `x-current-token-count` and `X-Next-Replenishment-Time` and sleep until
  replenishment. There is no `Retry-After`.
- On `423 RESOURCE_IS_LOCKED.GMP_RECEIVER_API`, back off; if it persists for an hour, reduce concurrency.

## References

- Errors: `errors/walmart-problem-types.yml` — https://developer.walmart.com/us-marketplace/docs/error-codes
- Conventions: `conventions/walmart-conventions.yml`
- Rate limits: `rate-limits/walmart-rate-limits.yml`
