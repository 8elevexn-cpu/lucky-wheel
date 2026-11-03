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

