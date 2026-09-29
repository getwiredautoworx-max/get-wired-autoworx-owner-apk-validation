# Owner App Remaining Implementation Plan

Updated: 2026-09-29

## Current validated facts
- APK debug build passes in GitHub Actions.
- APK artifact exists for run 36554065673 and has not expired.
- Emulator smoke test is still running; do not call full APK validation complete until it finishes successfully.
- Current application is a WebView shell loading https://getwiredautoworx.co.za/.
- Application ID: za.co.getwiredautoworx.owner.
- Target/compile SDK 35; minimum SDK 23; version 1.0.1.

## Parallel implementation work

### A. Owner management surface
The production Owner experience must provide, either through the web app loaded by the APK or through native screens:
- Owner authentication and protected access
- Dashboard overview
- Products: add, edit, price, stock, SKU and product status
- Categories and subcategories
- Vehicle compatibility/fitment
- Catalogue/pricelist import
- Supplier/source verification workflow
- Orders and order references
- Customers
- Store settings

### B. Mobile critical paths
Test and keep usable on a phone:
- Owner login
- Dashboard load
- Product search/edit
- Stock update
- Catalogue import/file picker
- Order lookup
- Customer/order reference lookup
- Back navigation
- Offline/error states

### C. Store integration
Verify end-to-end:
- Storefront product/category data
- Prices use the established VAT + markup formula
- Stock changes propagate correctly
- Orders create correct order and customer references
- Owner changes do not expose unauthorized customer/order data
- Catalogue imports do not overwrite verified production stock accidentally

### D. Customer storefront final checks
- Homepage and navigation
- Categories/subcategories
- Search
- Product detail
- Fitment
- Cart
- Checkout
- Payment
- Order confirmation/reference
- Mobile responsiveness
- Error handling

### E. Release controls
- Keep APK validation repo isolated from production.
- No Replit credits.
- No Cloudflare credits.
- Do not change production DB/RLS without a concrete blocker.
- Validate all release-critical flows before production activation.

## Execution order
1. Finish GitHub emulator smoke validation.
2. Recover the validated APK artifact.
3. Physical-device APK test.
4. Complete Owner management surface/integration review and implementation.
5. Complete customer checkout/payment/order testing.
6. Final production readiness pass.
