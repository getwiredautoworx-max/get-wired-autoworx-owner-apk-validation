# Get Wired AutoWorx — Store ↔ Owner Data Flow

Updated: 2026-09-29

## Production data boundaries
- Supabase remains the system of record for products, categories, customers, orders, order_items, store_settings and vehicle_compatibility.
- The Owner APK is a control surface; it must not maintain a second product/order database.
- Customer storefront reads approved catalogue data and creates customer/order lifecycle records through the existing backend.

## Product lifecycle
1. Supplier/source data is collected into a staging/import process.
2. SKU identity, cost, source and category are validated before production write.
3. Advertised price is calculated as cost × 1.15 × 1.35 and stored/displayed as VAT-inclusive.
4. Existing verified stock is preserved unless an import explicitly contains a validated stock update.
5. Owner can review product status, price and stock after import.

## Order lifecycle
Customer storefront → cart → checkout → payment/reference capture → order creation → Owner order lookup → fulfilment/status update → customer confirmation.

## Safety controls
- No bulk import may delete or zero existing verified stock merely because a source row is absent.
- SKU is the primary catalogue identity for reconciliation.
- Pricing QA must flag any value that differs from the required formula.
- Owner actions that mutate production data should be authenticated and auditable.
