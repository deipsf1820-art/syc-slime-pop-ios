# SlimePop iOS

將 HTML5 Matter.js 網頁遊戲轉為 iOS 原生 App 的 Xcode/Capacitor 工程。

## 專案結構

- `www/` — Web 原始碼與離線資源
- `ios/App` — Capacitor 生成的 Xcode 專案
- `resources/` — App 圖示與啟動畫面資源（可選）

##  prerequisites

- Xcode 14+（建議 15.x）
- CocoaPods 或 Xcode SPM（本例使用 SPM）
- iOS 15+ 部署目標
- 具備 Apple Developer Team（Signing）

## quick start

```bash
# 1. 安裝依賴
npm install

# 2. 同步網站文件到原生專案
npx cap sync ios

# 3. 以 Xcode 開啟專案
npx cap open ios
```

## Xcode 建置設定

在 Xcode 裡手動完成這些步驟：

1. 選擇開發 Team（Signing & Capabilities）
2. Bundle ID 預設為 `com.syc.slimepop`
3. Display Name: `史萊姆大爆發`
4. Orientation 只勾選 Portrait
5. 修改 Deploy Info 與 General 設定完成後，按 Run 或 Product > Archive 產生 .ipa

## 自訂說明

- 鎖定直向（Portrait）只顯示 Portrait，已於 `ios/App/App/Info.plist` 設定。
- 遊戲 canvas 原始尺寸 400x600 會根據設備大小自動縮放，並保留安全區域。
- Matter.js 使用本地 `www/matter.min.js`，確保離線可玩。

## 已知限制

- 本機環境沒有完整 Xcode，無法直接執行 `xcodebuild`，因此 `.ipa` 請在 Apple Silicon Mac + Xcode 上完成封裝。
- 若要自動化 App Store 上傳，可以在 Xcode 中使用 `Product > Archive`。

## 修改 Web 內容

1. 編輯 `www/index.html`
2. 執行 `npx cap sync ios` 更新原生專案中的 Web 資源

## FAQ

Q: 可以打成 .ipa 嗎？  
A: 本機無 Xcode，因此 .ipa 必須在有 Xcode 的 Mac 上由 `Product > Archive > Distribute App` 產生。

Q: 遊戲能離線玩嗎？  
A: 可以，所有遊戲資源都在 App bundle 內部。

---
License: ISC
