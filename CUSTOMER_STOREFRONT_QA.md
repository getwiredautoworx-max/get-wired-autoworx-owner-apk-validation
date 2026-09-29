# Get Wired AutoWorx — Customer Storefront QA

Updated: 2026-09-29

## Test matrix
- [ ] Homepage loads on Android Chrome.
- [ ] Category list and subcategories load.
- [ ] Search returns matching SKUs/products.
- [ ] Product detail shows name, SKU, VAT-inclusive price and availability.
- [ ] Vehicle compatibility information displays where available.
- [ ] Add-to-cart works from product listing and detail views.
- [ ] Cart quantity changes and removal work.
- [ ] Checkout validates required customer/contact/delivery fields.
- [ ] Payment/reference flow returns a deterministic order reference.
- [ ] Successful order is visible to the Owner workflow.
- [ ] Customer confirmation shows the order reference.
- [ ] Failed/cancelled payment does not create a falsely paid order.
- [ ] Back navigation works without losing cart state.
- [ ] Network failure produces a usable error/retry state.
- [ ] Layout remains usable on narrow Android screens.

## Release evidence
Record pass/fail, device/browser, timestamp, and any order reference for every release-critical flow. Do not use real customer payment details for QA.
