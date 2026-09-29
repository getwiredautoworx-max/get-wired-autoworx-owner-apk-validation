# Get Wired AutoWorx — Owner APK Physical Device QA

Updated: 2026-09-29

## Device test
- [ ] Install the validated debug APK.
- [ ] Confirm application ID and launcher start.
- [ ] Confirm HTTPS storefront loads.
- [ ] Confirm JavaScript-dependent storefront functions work.
- [ ] Confirm file/content chooser opens and returns to the app.
- [ ] Confirm Android Back navigates WebView history correctly.
- [ ] Confirm app recovers from temporary network loss.
- [ ] Confirm rotation/background-resume does not corrupt the active flow.
- [ ] Confirm no production credentials or secrets are bundled in the APK.

## Release note
Emulator smoke validation proves build/install/launch. Physical-device testing is a separate release check and must use the validated artifact.
