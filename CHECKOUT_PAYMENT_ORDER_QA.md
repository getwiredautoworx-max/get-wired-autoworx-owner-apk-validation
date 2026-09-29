# Get Wired AutoWorx — Checkout / Payment / Order QA

Updated: 2026-09-29

## Required scenarios
1. Valid cart → checkout → successful payment/reference → one order with correct items, quantities and total.
2. Payment failure → no order marked paid.
3. Payment cancellation/abandonment → no false successful confirmation.
4. Duplicate callback/retry → no duplicate paid order for the same payment event.
5. Customer/order reference is generated once and remains stable.
6. VAT-inclusive displayed totals equal the backend order totals.
7. Stock is not decremented twice on repeated payment callbacks.
8. Owner can locate the order by customer and order reference.

## Reconciliation
For each successful test, compare storefront total, payment/reference total and stored order total. Any mismatch blocks production activation until corrected.
