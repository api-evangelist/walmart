---
name: walmart-order-cancel-refund
description: Reverse a Walmart Marketplace order — cancel before shipment, refund after — and know exactly which window each one lives in.
api: Walmart Orders API
generated: '2026-08-27'
method: generated
source: openapi/walmart-orders-api-openapi.yml, conventions/walmart-conventions.yml (reversibility block)
operations:
  - getAnOrder
  - cancelOrderLines
  - refundOrderLines
---

# Undo a Walmart order

Walmart splits reversal into two operations with different boundaries. Pick by the order's current state, not by elapsed time.

## Steps

1. **Read the current state first.** `getAnOrder` — `GET /v3/orders/{purchaseOrderId}`. You need the line statuses and any
   prior refund amounts before you can decide.
2. **Cancel, if nothing has shipped.** `cancelOrderLines` — `POST /v3/orders/{purchaseOrderId}/cancel`. Limit 60/min.
   - Window: only while the order is **neither shipped nor already cancelled**.
   - Cancelling a shipped or cancelled order returns `400 INVALID_REQUEST`.
3. **Refund, if it has shipped.** `refundOrderLines` — `POST /v3/orders/{purchaseOrderId}/refund`. Limit 60/min.
   - Window: the refund amount must fall within the **remaining allowable amount** after prior partial refunds. Exceeding it
     returns `400 INVALID_REQUEST`.
   - Walmart states **no calendar window** for refunds. Do not assume a 30/60/180-day limit; sum prior refunds and compute
     the remaining allowance from the order itself.

## Rules that will bite you

- **There is no idempotency key.** A refund POST that times out may or may not have landed. Re-read the order with
  `getAnOrder` and recompute prior refunds before retrying — a blind retry can double-refund a customer.
- A refund is not reversible. There is no un-refund operation.
- Orders auto-cancel if not shipped within 30 days; a cancel on an already-auto-cancelled order will fail.

## References

- Reversibility matrix: `conventions/walmart-conventions.yml`
- Errors: https://developer.walmart.com/us-marketplace/docs/error-codes
