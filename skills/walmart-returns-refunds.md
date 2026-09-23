---
name: walmart-returns-refunds
description: Work the Walmart Marketplace returns queue — read return orders, issue the refund, and respect the state conditions that gate each step.
api: Walmart Returns/Refunds API
generated: '2026-08-27'
method: generated
source: openapi/walmart-returns-refunds-api-openapi.yml, conventions/walmart-conventions.yml
operations:
  - getReturns
  - issueRefund
---

# Handle a Walmart return

## Steps

1. **Read the queue.** `getReturns` — `GET /v3/returns`. Limit 50/min. Filter by return status and date range; paginate before
   you widen the window.
2. **Refund.** `issueRefund` — `POST /v3/returns/{returnOrderId}/refund`. Limit 60/min.

For WFS/Multichannel returns the surface is different: `POST /v3/fulfillment/return-orders` creates a customer return order
(60/min), `GET /v3/fulfillment/return-orders` reads status (60/min), and
`POST /v3/fulfillment/return-orders/{orderId}/cancel` cancels one (60/min).

## Rules that will bite you

- **A refund is the reversal. It is not itself reversible.** There is no un-refund operation anywhere in the Walmart surface.
- **There is no idempotency key.** If `issueRefund` times out, re-read the return before retrying — a blind retry can refund
  the customer twice.
- A WFS return order can only be cancelled **while at least one line is in `RETURN_INITIATED` status**; otherwise you get
  `400 "Return order cannot be cancelled"`.
- Creating a WFS return fails with `400.WFS.100` if the SKU is not on the original order, and with `500.509` if the requested
  quantity is zero or exceeds the ordered quantity.
- A line must be in `DELIVERED` status to be eligible for a return; otherwise `400 "Order status not eligible for returns"`.
- Subscribe to the `RETURN_NOTIFICATIONS` webhook instead of polling `getReturns` on a short timer.

## References

- Error catalogue: `errors/walmart-problem-types.yml`
- Reversibility matrix: `conventions/walmart-conventions.yml`
