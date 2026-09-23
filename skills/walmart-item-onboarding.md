---
name: walmart-item-onboarding
description: Get items into the Walmart catalogue — submit the item feed, track ingestion, then confirm the listing is live and searchable.
api: Walmart Items API
generated: '2026-08-27'
method: generated
source: openapi/walmart-items-api-openapi.yml, openapi/walmart-feeds-api-openapi.yml, conformance/walmart-conformance.yml
operations:
  - getSpec
  - itemBulkUploads
  - getFeedItemStatus
  - getAllItems
  - getAnItem
  - getCatalogSearch
  - retireAnItem
---

# Onboard items to Walmart Marketplace

## Steps

1. **Fetch the current item spec.** `getSpec` — `POST /v3/items/spec`. Limit 10/min. The Item Spec has its own version stream
   (currently 5.0) that moves independently of the `/v3` API version — always generate your payload from the live spec, never
   from a cached copy.
2. **Submit the feed.** `itemBulkUploads` — `POST /v3/feeds?feedType=MP_ITEM`. Limit **10/hour**, max file 25 MB.
   Returns a `feedId`.
3. **Track ingestion.** `getFeedItemStatus` — `GET /v3/feeds/{feedId}`. Poll at 15 min, 1 h, 2 h, then every 4 h.
   Item-level failures come from `GET /v3/feeds/{feedId}/errorReport`.
4. **Confirm the listing.** `getAnItem` — `GET /v3/items/{id}` (900/min, but 60/min if you use query parameters), or
   `getAllItems` — `GET /v3/items` (300/min, 60/min with query parameters).
5. **Search the catalogue.** `getCatalogSearch` — `POST /v3/items/catalog/search`. Limit 200/min, shared with
   Get Item Associations. Body takes `query {field,value}` (with `%` wildcards), `filters[] {field,op,values[]}` and
   `sort {field,order}`. Paginate with `page`/`limit` or with `nextCursor` (send `*` first; it expires in 2 minutes).

## Identifiers

Walmart is a GS1 shop. `gtin` is a **14-digit** GTIN including the check digit — zero-pad shorter numbers on the left. `upc`,
`ean` and `isbn` are accepted alongside your own `sku`. If a product legitimately has no GS1 identifier, check eligibility at
`GET /v3/items/gtin-exemption/status` (100/min) rather than inventing one.

## Rules that will bite you

- **Updating an item that has not finished ingesting returns `404 CONTENT_NOT_FOUND`.** Check feed status before you update.
- `retireAnItem` — `DELETE /v3/items/{SKU}` (900/min) — is **not undoable by API**. A retired SKU must be re-ingested through
  the Feeds API.
- A published offer emits an `OFFER_PUBLISHED` webhook; subscribe to it rather than polling `getAllItems` in a loop.

## References

- Data model: `data-model/walmart-data-model.yml`
- Domain standards (GS1 GTIN): `conformance/walmart-conformance.yml`
