# Get Wired AutoWorx — Owner App Remaining Implementation Plan

Updated: 2026-09-29

## Completed
- GitHub Actions build validation: PASS.
- Emulator APK build/install/launch validation: PASS (run 36560104394).
- Validated debug artifact recovered/available.
- Timeout-controlled emulator validation is working.
- Store/Owner data-flow, catalogue controls, storefront QA, checkout QA and physical-device QA documentation created.

## Current implementation state
The APK itself is a lightweight WebView shell loading the production HTTPS storefront. Native APK build validation is complete, but the richer Owner management experience is not yet implemented in this repository.

## Owner management surface still required
- Owner authentication and protected access
- Dashboard overview
- Products: add/edit/price/stock/SKU/status
- Categories/subcategories
- Vehicle compatibility/fitment
- Catalogue/pricelist import
- Supplier/source verification
- Orders and order references
- Customers
- Store settings

## Execution blockers
The remaining implementation cannot be truthfully marked complete from APK smoke testing alone. The live web application and Supabase-backed Owner routes must be inspected and tested before claiming these functions work.

## Release checks still required
1. Physical-device installation using artifact 11028368736.
2. Owner web/dashboard route and authentication test.
3. Product/category/stock/order/customer integration test.
4. Controlled catalogue import test against an approved source file.
5. Customer storefront mobile QA.
6. Checkout/payment/order-reference test using approved test/payment details.
7. Security/usability/readiness review.
8. Production activation only after release-critical checks pass.

## Hard controls
- No Replit credits.
- No Cloudflare credits.
- Do not alter production DB/RLS unless a concrete blocker is found.
- Do not import the historically incorrect 1,109-row extraction.
