# Get Wired AutoWorx — Owner APK / Store Handover

Updated: 2026-09-29

## Completed — Owner APK validation work
- Isolated public validation repository created and accessible:
  `getwiredautoworx-max/get-wired-autoworx-owner-apk-validation`.
- GitHub Actions build workflow created and operational.
- Previous emulator blocker identified: hard-coded `Pixel_2` AVD profile was incompatible with the hosted runner.
- Removed the hard-coded Pixel_2 profile and committed the compatibility fix.
- Validation run #11 started successfully after the fix.
- Run #11 build job completed successfully.
- Debug APK compilation succeeded.
- SHA-256 checksum generation succeeded.
- Debug APK artifact upload succeeded.
- Emulator-side APK build succeeded.
- Run #11 emulator installation/launch smoke test is still in progress; final validation is therefore NOT yet marked complete.

## Completed — APK/code/workflow audit
- Package/application ID confirmed: `za.co.getwiredautoworx.owner`.
- Launcher activity confirmed: `za.co.getwiredautoworx.owner/.MainActivity`.
- Compile SDK: 35.
- Target SDK: 35.
- Minimum SDK: 23.
- Version: 1.0.1 / versionCode 2.
- INTERNET permission confirmed.
- HTTPS production-store loading confirmed.
- WebView JavaScript and DOM storage enabled.
- WebView file/content access and file chooser support confirmed.
- Back-navigation handling confirmed.
- Emulator workflow confirmed: API 35, Google APIs, x86_64, with no hard-coded AVD profile.
- Current APK is a WebView-based Owner shell loading the production store URL. It is not yet being treated as a fully native Owner management dashboard.

## Completed — production store/database baseline
- Supabase production database remains established and separate from APK validation.
- Existing public tables: categories, customers, order_items, orders, products, store_settings, vehicle_compatibility.
- RLS remains enabled on the seven production tables.
- Public read policies for products/categories were already established; no further DB/RLS work is currently required for this validation phase.
- Pricing formula remains: cost × 1.15 VAT × 1.35 markup; displayed price is VAT-inclusive.
- Latest catalogue baseline retained: approximately 4,188 unique priced SKUs / 4,198 active products; 0 uncategorized; 44 products with stock; 7,077 total in-stock units; 36 SKUs / 7,037 units independently verified against ASC; pricing formula verified with no mismatches.
- Existing production storefront package remains: `Get_Wired_AutoWorx_Storefront_Stage2_Live.zip`, with live catalogue loading, search, category filtering, mobile storefront and browser cart.
- Production database/store has not been modified as part of the isolated APK validation.

## Remaining — immediate APK validation
1. Wait for run #11 emulator smoke test to finish.
2. Confirm APK installation succeeds on the hosted Android emulator.
3. Confirm `MainActivity` launches successfully.
4. Confirm final workflow/run conclusion is successful.
5. Confirm/recover the generated APK artifact and checksum.
6. Update this handover immediately when validation is actually complete.

## Remaining — after APK validation
1. Retrieve the validated APK artifact.
2. Perform live-device installation/testing on a physical Android device.
3. Test launch, WebView loading, navigation, file picker and basic Owner/store interaction on-device.
4. Review Owner-app requirements against the current WebView shell.
5. If required features are not already present, implement the richer Owner management dashboard rather than assuming the shell is feature-complete.
6. Continue Owner app ↔ store integration checks.
7. Complete final customer-facing storefront/live-store readiness checks.
8. Verify checkout/payment/order-reference flows before production activation.
9. Perform final mobile usability and critical-path checks.
10. Only then proceed to full live-store activation.

## Explicit project constraints
- NO Replit credits are to be used.
- NO Cloudflare credits are to be used.
- Do not disturb the production store/database while APK validation is in progress.
- Do not redo completed Supabase/database work unless a concrete blocker requires it.
- Update this handover after each meaningful completed task execution.
- User requested notification only when APK validation is actually completed, unless an input/action is absolutely necessary.

## Current status
- APK build: COMPLETE / PASS.
- APK checksum: COMPLETE / PASS.
- APK artifact upload: COMPLETE / PASS.
- Emulator APK build: COMPLETE / PASS.
- Emulator install/launch smoke test: IN PROGRESS.
- Full APK validation: PENDING emulator completion.
- Physical-device testing: NOT STARTED.
- Rich Owner dashboard review/implementation: REMAINING.
- Store/app integration checks: REMAINING.
- Final live-store readiness checks: REMAINING.
