# Get Wired AutoWorx — Owner APK / Store Handover

Updated: 2026-09-29 — post Owner APK/admin integration

## APK validation — RUN #23 PASSED
- GitHub Actions workflow run ID: 36560104394.
- Commit: `4c720c2103ea47b975002da40488b904a5793c27`.
- Build job: SUCCESS.
- Debug APK compilation: SUCCESS.
- SHA-256 checksum: SUCCESS.
- APK artifact upload: SUCCESS.
- Emulator APK build: SUCCESS.
- Android emulator smoke test: SUCCESS.
- Emulator job conclusion: SUCCESS.
- The timeout-controlled emulator job completed successfully; the previous hanging validation condition is resolved.
- APK artifact ID: 11028368736.
- Artifact digest: sha256:a6f41d87103d28aae941ce871176bfd36a1dccf9071da0bea7a993738d71e894.
- Artifact expires: 2026-12-28.
- Future HANDOVER.md and ALTERNATE_TASKS_EXECUTION_STATUS.md changes are excluded from the validation workflow trigger, preventing a handover-update loop.

## APK/code audit
- Application ID: `za.co.getwiredautoworx.owner`.
- Launcher activity: `za.co.getwiredautoworx.owner/.MainActivity`.
- Compile/target SDK 35; minimum SDK 23.
- Version 1.0.1 / versionCode 2.
- INTERNET permission confirmed.
- HTTPS production-store loading.
- JavaScript + DOM storage enabled.
- File/content access and file chooser support.
- Back navigation support.
- Current APK is a WebView-based Owner control surface and now opens the protected store admin portal at `/admin.html` instead of the customer storefront. The admin portal itself was verified in the store repository and provides Supabase Auth OTP login plus order-management RPC controls. Live authenticated execution remains required.

## Parallel work completed
- Owner management scope documented.
- Store code audit completed; existing protected admin portal, checkout, order RPC integration and shipping-quote endpoint verified from the store repository.
- Netlify hosting verified: production deploy is READY but is still on store commit `37654d7c2e8e38dad80f9edf33413aa1be62d1a4` and reports no deployed functions; current repository changes therefore still require a real source deployment before live storefront/checkout QA can be signed off. Netlify environment configuration was also verified and points to the correct Supabase project; no payment/shipping secret credentials were added or altered.
- Production order RPCs hardened and verified: corrected delivery-fee validation, atomic stock reservation/restoration, pinned SECURITY DEFINER search paths, and tighter RPC execution roles. Remaining public create_store_order SECURITY DEFINER advisory is intentional for anonymous storefront checkout.
- Owner APK updated to version 1.0.2 / versionCode 3 and routed directly to the protected admin portal.
- Mobile critical paths documented.
- Store ↔ Owner data-flow controls documented in `STORE_OWNER_DATA_FLOW.md`.
- Catalogue/pricelist import controls documented in `CATALOGUE_IMPORT_CONTROL.md`.
- Customer storefront QA matrix documented in `CUSTOMER_STOREFRONT_QA.md`.
- Checkout/payment/order QA matrix documented in `CHECKOUT_PAYMENT_ORDER_QA.md`.
- Physical-device QA checklist documented in `PHYSICAL_DEVICE_QA.md`.
- Production store/database was not modified.
- No Replit credits used.
- No Cloudflare credits used.

## Remaining release tasks
1. Physical-device installation and validation using the validated artifact.
2. Complete validation of the updated Owner APK build/emulator run.
3. Execute live authenticated Owner ↔ Supabase/store integration checks.
4. Execute controlled catalogue/pricelist import and supplier verification against approved source data.
5. Execute customer storefront QA on the live store.
6. Execute checkout/payment/order-reference tests with approved payment/test details.
7. Final production security/usability/readiness pass.
8. Production activation only after release-critical checks pass.

## Current status
- APK CI build: PASS.
- APK emulator install/launch validation: PASS.
- APK validation blocker: RESOLVED.
- Validated artifact: AVAILABLE.
- Physical-device testing: NOT STARTED.
- Owner management surface: EXISTING PROTECTED WEB ADMIN PORTAL VERIFIED; APK ROUTING UPDATED; LIVE AUTHENTICATED TEST REMAINS.
- Store integration: EXECUTION REMAINING.
- Customer checkout/payment/order testing: EXECUTION REMAINING.
- Final live-store readiness: REMAINING.
