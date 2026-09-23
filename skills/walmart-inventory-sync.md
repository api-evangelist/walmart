---
name: walmart-inventory-sync
description: Keep Walmart Marketplace inventory in step with your own — single-SKU updates for hot changes, bulk feeds for the nightly reconcile.
api: Walmart Inventory API
generated: '2026-08-27'
method: generated
source: openapi/walmart-inventory-api-openapi.yml, openapi/walmart-feeds-api-openapi.yml, rate-limits/walmart-rate-limits.yml
operations:
  - getInventory
  - putUpdateInventory
  - postBulkUpdateInventory
  - getAllFeedStatuses
  - getFeedItemStatus
---

# Sync inventory to Walmart

Two paths, and choosing the wrong one is the most common cause of throttling.

## Path A — single SKU, synchronous

1. **Read.** `getInventory` — `GET /v3/inventory?sku={sku}`. Limit 200/min.
2. **Write.** `putUpdateInventory` — `PUT /v3/inventory?sku={sku}`. Limit 200/min.
3. Per ship node: `GET /v3/inventories/{sku}` and `PUT /v3/inventories/{sku}`, both 200/min.

Use this for reactive changes — a sale just happened, a stockout just occurred. Do **not** loop it over a whole catalogue.

## Path B — bulk, asynchronous via Feeds

1. **Submit.** `postBulkUpdateInventory` — `POST /v3/feeds?feedType=inventory`. Limit **10/hour**, max file 10 MB.
   The `mp_inventory` feed type is 50/hour with a 1 MB cap; `dsv_inventory` is 50/hour with a 10 MB cap.
   The response returns a `feedId`.
2. **Poll.** `getFeedItemStatus` — `GET /v3/feeds/{feedId}`. Walmart's recommended polling schedule is
   **15 minutes, then 1 hour, then 2 hours, then every 4 hours**. Keep calling while the status is `INPROGRESS` or
   `PROCESSING`.
3. **Read failures.** When the status reaches `PROCESSED`, item-level errors are downloaded from
   `GET /v3/feeds/{feedId}/errorReport` (60/hour).
4. **List recent feeds.** `getAllFeedStatuses` — `GET /v3/feeds`. Limit 5000/min, shared with `getFeedItemStatus`.

## Rules that will bite you

- **Feed limits are per hour, not per minute.** At 10/hour you get one submission every six minutes; batch accordingly.
- A file over the cap returns `413 Payload Too Large`, not a 400.
- **There is no idempotency key.** Re-submitting the same feed creates a second feed run. If a submission times out, call
  `getAllFeedStatuses` and look for a feed you already created before re-sending.
- Feed statuses: `ERROR` (file rejected or failed), `INPROGRESS` (accepted / processing), `PROCESSED` (done — may still carry
  per-record errors in the error report).
- `ERR_PDI_0001` means the whole file failed to parse; `ERR_PDI_0034` means required fields are missing or invalid. Revalidate
  against the latest XSD before resubmitting.

## References

- Rate limits (all 202 published limits): `rate-limits/walmart-rate-limits.yml`
- Errors: https://developer.walmart.com/us-marketplace/docs/error-codes
