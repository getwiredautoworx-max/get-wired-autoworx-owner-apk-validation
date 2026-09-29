# Get Wired AutoWorx — Live Store Code Audit
Updated: 2026-09-29

## Verified from the store repository
- Customer storefront is in `index-new.html` and is Supabase-backed.
- A protected staff portal exists at `admin.html`.
- The admin portal uses Supabase Auth OTP sign-in and RPCs `admin_list_orders` and `admin_update_order`.
- Admin order controls include order status, payment status, payment reference, internal notes and WhatsApp customer contact.
- Checkout exists at `checkout.html` and validates the cart against active Supabase products before order creation.
- Storefront checkout enhancement exists in `assets/store-enhancements.js` and submits orders through `create_store_order`.
- Delivery quote endpoint exists at `netlify/functions/shipping-quote.ts`, exposed as `/api/shipping/quote`.
- Shipping code supports configured live providers through server-side environment variables and PAXI published fixed pricing for supported parcel weights.
- The checkout currently exposes EFT/manual payment/cash-on-pickup style flows; a live card gateway is not enabled by the inspected checkout code.
- Payment remains pending until store-side confirmation in the current checkout implementation.

## Owner APK integration change
The Owner APK now opens `https://getwiredautoworx.co.za/admin.html` rather than the customer storefront, so the APK is aligned to the existing protected staff portal.

## Still requiring live execution
- Authenticate through the live admin portal with an authorised staff account.
- Confirm admin RPCs work against production Supabase data.
- Run a controlled test order and reconcile storefront → Supabase → admin order reference.
- Verify payment/reference behaviour with approved test details.
- Verify live delivery quote behaviour where provider credentials are configured.
- Complete physical-device APK validation.

## Safety
- No production catalogue/database mutation performed by this audit.
- The historical incorrect 1,109-row extraction remains prohibited.
- No Replit credits used.
- No Cloudflare credits used.
