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

## Database integration hardening completed
- Verified production Supabase counts: 4,187 active products, 107 active categories, 4,198 products with stock_quantity > 0, 0 pricing mismatches, 0 active products missing SKU.
- Verified required RPCs exist: create_store_order, admin_list_orders, admin_update_order.
- Hardened the three order/admin RPCs with an empty SECURITY DEFINER search_path and fully qualified table references.
- Corrected order validation so pickup/manual/EFT orders are not rejected solely because the delivery fee is zero; non-negative quoted delivery fees are accepted.
- Stock is reserved atomically when an order is created and is restored when an order is cancelled, failed or refunded, with safeguards against repeated restoration.
- Restricted Owner/admin RPC execution roles; the public create_store_order RPC remains intentionally callable by anonymous storefront users because the customer checkout is public.
- Supabase security advisor was rechecked. The remaining SECURITY DEFINER warning for create_store_order is intentional because the public storefront must call it; admin RPCs are not anonymous-callable.

## Hosting verification
- Netlify project `get-wired-autoworx-store` exists and its current production deploy is READY.
- Current Netlify production deploy ID: `6aa98a8a679a4a0008e10b58`.
- That deployed build is from store commit `37654d7c2e8e38dad80f9edf33413aa1be62d1a4` dated 2026-09-24.
- Netlify reports no functions in that deployed build, so the current deployed site is not yet carrying the repository's newer shipping-quote function.
- A Netlify deploy action was initiated/validated, but the available Netlify connector requires the repository source directory to be present for the actual upload; no production deploy was falsely marked complete.
