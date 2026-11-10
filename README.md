# Vanya Retreat – Android app

Android app (WebView) for https://vanyaretreat.in.
Package ID: `in.vanyaretreat.app`

Every push to `main` builds on GitHub Actions and produces:
- **VanyaRetreat-N.apk** – install directly on phones
- **VanyaRetreat-N.aab** – upload to Google Play Console

## Download the builds
GitHub repo → **Actions** → latest "Build Android APK and AAB" run → **Artifacts** at the bottom.
Run a build manually with **Actions → Build Android APK and AAB → Run workflow**.

## Signing (needed for Play Store)
Add these under **Settings → Secrets and variables → Actions → New repository secret**:

| Secret | Value |
|---|---|
| `KEYSTORE_BASE64` | contents of `KEYSTORE_BASE64.txt` |
| `KEYSTORE_PASSWORD` | from `SIGNING-KEY-DETAILS.txt` |
| `KEY_ALIAS` | `vanya-upload` |
| `KEY_PASSWORD` | from `SIGNING-KEY-DETAILS.txt` |

Without these, the APK still works but the AAB is debug-signed and Play Store will reject it.
Never commit the `.jks` file to this repo.

## Changing things
- Website address: `START_URL` / `SITE_HOST` in `app/build.gradle.kts`
- App name: `app/src/main/res/values/strings.xml`
- Colours: `app/src/main/res/values/colors.xml`
- Icons: `app/src/main/res/mipmap-*`

Version code goes up automatically with each GitHub build number.
