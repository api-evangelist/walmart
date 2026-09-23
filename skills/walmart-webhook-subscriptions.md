---
name: walmart-webhook-subscriptions
description: Subscribe to Walmart Marketplace events instead of polling — register a destination, verify delivery, and handle the envelope.
api: Walmart Notifications API
generated: '2026-08-27'
method: generated
source: openapi/walmart-notifications-api-openapi.yml, asyncapi/walmart-webhooks.yml
operations:
  - getEventTypes
  - createSubscription
  - getAllSubscriptions
  - updateSubscription
  - deleteSubscription
  - testNotification
---

# Subscribe to Walmart Marketplace events

Polling `GET /v3/orders` on a timer burns your 5000/min bucket for nothing. Subscribe instead.

## Steps

1. **List what you can subscribe to.** `getEventTypes` — `GET /v3/webhooks/eventTypes`. Limit **5/min** — cache the result.
2. **Register a destination.** `createSubscription` — `POST /v3/webhooks/subscriptions`. Limit 200/min. Supply the event type
   and your HTTPS `eventUrl`. Walmart POSTs `application/json` to that URL.
3. **Verify delivery.** `testNotification` — `POST /v3/webhooks/test`. Limit 10/min. Fires a synthetic delivery at your
   registered URL so you can confirm the endpoint before real traffic arrives.
4. **Audit.** `getAllSubscriptions` — `GET /v3/webhooks/subscriptions`. Limit 50/min.
5. **Change or remove.** `updateSubscription` — `PATCH /v3/webhooks/subscriptions/{subscriptionId}` (5/min);
   `deleteSubscription` — `DELETE /v3/webhooks/subscriptions/{subscriptionId}` (10/min). Both are fully reversible: you can
   re-create a deleted subscription at any time.

## The envelope

Every delivery carries `eventType`, `eventVersion`, `eventTime`, `eventId` and a `payload` whose shape varies by event type.
Key off `eventType` and treat `payload` defensively — Walmart does not publish per-event payload schemas.

## The thirteen event types

`OFFER_PUBLISHED`, `OFFER_UNPUBLISHED`, `BUY_BOX_CHANGED`, `INVENTORY_OOS`, `PO_CREATED`, `PO_LINE_AUTOCANCELLED`,
`ORDER_INTENT_TO_CANCEL`, `ORDER_MANAGEMENT_EVENT`, `DRIVER_STATUS_NOTIFICATION`, `RETURN_NOTIFICATIONS`, `REPORT_STATUS`,
`ASSORTMENT_RECOMMENDATIONS`, `SELLER_PERFORMANCE_NOTIFICATIONS`.

## Rules that will bite you

- **Walmart publishes no AsyncAPI for this surface.** `asyncapi/walmart-marketplace-notifications-asyncapi.yml` in this repo is
  an API Evangelist derivation from the documented catalogue, not a Walmart artifact — do not treat its payload schemas as
  authoritative.
- `getEventTypes` at 5/min is one of the tightest limits on the platform. Cache it; do not call it per subscription.
- `REPORT_STATUS` is the correct way to learn an on-request report finished. Do not poll `GET /v3/reports/reportRequests/{id}`,
  which is capped at 20/hour.

## References

- Event catalogue: `asyncapi/walmart-webhooks.yml`
