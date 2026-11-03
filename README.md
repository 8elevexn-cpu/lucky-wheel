# 幸運轉盤 APK 專案

- 套件名稱：`tw.lucky.wheel`　版本：versionCode 6／1.0.5
- 網頁內容在 `app/src/main/assets/index.html`，之後要改畫面，換掉這個檔案再推上去即可。
- 推上 `main` 分支後，GitHub Actions 會自動編譯，完成後到 **Actions → 最新一次 → Artifacts** 下載 `lucky-wheel-apk`。

## 用原金鑰簽名（才能覆蓋安裝舊版）
到儲存庫 **Settings → Secrets and variables → Actions → New repository secret** 新增：

| 名稱 | 內容 |
|---|---|
| KEYSTORE_BASE64 | 金鑰檔轉成的 Base64 文字（用附的「金鑰轉Base64工具.html」產生） |
| KEYSTORE_PASSWORD | 金鑰庫密碼 |
| KEY_ALIAS | `lucky-wheel` |
| KEY_PASSWORD | 金鑰密碼（若與金鑰庫密碼相同可不填） |

沒設定時仍可編譯，但會用 debug 金鑰，無法覆蓋舊版。
**金鑰檔與密碼絕對不要放進儲存庫。**

## 網頁版
根目錄的 `index.html` 就是網頁版（GitHub Pages）；`app/src/main/assets/index.html` 是打包進 APK 的同一份，改畫面時兩邊都要換。
