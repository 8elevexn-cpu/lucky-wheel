# Lucky Wheel — A Colorful, Multi-Wheel Prize Draw System

[中文](README.md) ｜ **English**

A single-file HTML prize wheel that runs in any browser and can also be packaged as an Android app (APK).
Current version: **1.0.6** (APK versionCode 7, package name `tw.lucky.wheel`)

---

## Features

- **Multiple wheels** — create, switch, export and import as many wheels as you like. Each wheel keeps its own items and settings.
- **Per-wheel winner history** — switching wheels shows that wheel's history and its latest result. "Clear history" only clears the current wheel, and history is kept and continued after you reopen the app.
- **Five color themes** — Vibrant Carnival, Vegas Gold, Cyber Neon, Pastel Candy, Forest Emerald.
- **Two draw modes**
  - Keep winners: a drawn item stays on the wheel
  - Auto-remove winners: a drawn item is removed from the wheel immediately
- **Sound** — built-in synthesized sound, custom sound upload (MP3/WAV), mute, and a preview button.
- **Text settings** — wheel text size (auto, 18–64, or custom) and color are adjustable. When you choose a size it is used as-is; names that are too long are shortened with "…".
- **Fullscreen mode** — handy for projectors and live events.
- **Glowing "Start" button**, which pauses its glow and is disabled while the wheel is spinning.
- **Small-phone layout** — the settings bar is compacted into one row and respects the status bar and navigation bar.
- Templates when creating a wheel: blank, "What's for dinner?", Truth or Dare, Lucky Number (1–10).

## How to use

1. Open the web page (or the app), go to the **Wheel** tab and press **Start**.
2. Use the controls at the top to quickly switch wheel, theme, draw mode and sound.
3. In the **Wheel Manager** tab you can:
   - Add wheels and edit a wheel's name, color theme and draw rule
   - Edit the items (**one per line**) and press "Save and update wheel"
   - Configure sound
   - **Export / import** a backup of all wheels
4. Use **History** to view the current wheel's winners, and clear them if needed.

## Data storage and backups

- Wheels and winner history are stored in the **local storage of that browser or app**. Nothing is uploaded to a server.
- Clearing browser data, switching browsers or phones, or **uninstalling the app** removes your data.
- Please **export** a backup from the Wheel Manager regularly; the export also contains each wheel's winner history.
- When exporting inside the app, the file is saved to the phone's Downloads folder.

## Web version (GitHub Pages)

1. Push this project to the `main` branch of your repository.
2. Go to **Settings → Pages** and set Source to **GitHub Actions**.
3. Every push deploys automatically to `https://<username>.github.io/<repository>/`.

The root `index.html` is the web version. `app/src/main/assets/index.html` is the same page bundled into the APK, so **replace both** when you change the UI.

## Android app (APK)

- The project contains an Android project and a GitHub Actions workflow (`.github/workflows/build-apk.yml`).
- After pushing, wait for "Build APK" to finish in **Actions**, then:
  - Open **Releases** on the repository home page and download `lucky-wheel-v1.0.6.apk`
  - Or download it from **Artifacts** at the bottom of the workflow run page
- If installation is blocked, allow your browser to "install unknown apps" in the phone settings.

### Signing key (required to update an existing install)

Add these under **Settings → Secrets and variables → Actions**:

| Name | Value |
|---|---|
| `KEYSTORE_BASE64` | Your keystore (.jks) file converted to Base64 text |
| `KEYSTORE_PASSWORD` | Keystore password |
| `KEY_ALIAS` | Key alias (`lucky-wheel`) |
| `KEY_PASSWORD` | Key password (optional if identical to the keystore password) |

- Without these secrets the app still builds, but it is signed with a debug key and **cannot update an install that was signed with your release key**.
- The build log prints the signing certificate's SHA-256 — compare it with your previous release to confirm they match.
- **Never commit the keystore or its password to the repository** (`.gitignore` already excludes `*.jks`, `*.keystore` and `signing-password*.txt`).
- When releasing an update, raise `versionCode` in `app/build.gradle` so Android treats it as an upgrade.

## Project structure

```
index.html                     Web version (single file)
app/                           Android project (WebView wrapper)
  src/main/assets/index.html   Page used inside the APK
  src/main/java/tw/lucky/wheel/MainActivity.java
.github/workflows/
  pages.yml                    Deploys GitHub Pages
  build-apk.yml                Builds the APK and publishes it to Releases
```

## Notes

- The page loads its styles and fonts over the internet, so a network connection is required.
- On Android 15 and later, the app automatically keeps content clear of the status bar and navigation bar.
