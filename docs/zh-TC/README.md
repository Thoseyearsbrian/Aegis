<!-- Aegis Logo -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/logos/aegis-logo.png" alt="Aegis Logo"/>
</p>

<h1 align="center">Aegis</h1>
Surge 個人數位防火牆規則集，幫助使用者在 iOS 與 macOS 本地實現流量的精準識別與分類，並根據自身需求自主設定流量策略。支援簡體中文、繁體中文與 English 三種語言，助力全球使用者快速部署與靈活使用。

<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/screenshots/group-policy-mobile-tc-1.png" width="300" alt="Surge iOS：Aegis_TC 配置概覽介面截圖" />
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/screenshots/group-policy-mobile-tc-2.png" width="300" alt="Surge iOS：Aegis_TC 策略群組介面截圖" />
</p>

<p align="center">
  [<a href="https://github.com/Thoseyearsbrian/Aegis/blob/main/docs/zh-CN/README.md">简体中文</a>]
  [<a href="https://github.com/Thoseyearsbrian/Aegis/blob/main/docs/zh-TC/README.md">繁體中文</a>]
  [<a href="https://github.com/Thoseyearsbrian/Aegis/blob/main/docs/en-US/README.md">English</a>]
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License: Apache 2.0" />
  <img src="https://github.com/Thoseyearsbrian/GeoIP2-Country/actions/workflows/update.yml/badge.svg" alt="GeoIP2-Country Auto Update Status" />
  <img src="https://img.shields.io/github/v/release/Thoseyearsbrian/Aegis?include_prereleases&label=version" alt="Version" />
  <img src="https://img.shields.io/github/last-commit/Thoseyearsbrian/Aegis" alt="Last Commit" />
  <img src="https://img.shields.io/github/stars/Thoseyearsbrian/Aegis?style=social" alt="GitHub stars" />
  <a href="https://github.com/Thoseyearsbrian/Aegis">
  <img src="https://img.shields.io/badge/Mirror--Prohibited-red" alt="Mirror Prohibited" />
  </a>
</p>

## 專案優勢

Aegis 專為 [Surge](https://nssurge.com) 平台設計，全面相容 iOS 與 macOS 系統，具備良好的可讀性、可審計性與模組化部署能力，適用於策略分流、通訊識別與安全輔助設定等多種應用場景。

本專案全面採用加密 DNS，拒絕明文請求，確保通訊加密與隱私安全。即便在如 iPhone 等缺乏傳統安全軟體支援的裝置上，亦可提供流量層級的有效防護。

## 專案理念

Aegis 是一個堅持技術中立、資訊透明、獨立自主的安全規則專案。我堅信每個人都應擁有對其網路流量的知情權與控制權。因此，Aegis 不接受任何形式的商業投資或資本控制，為保持純粹的獨立性與安全可信性，所有設定檔完全由本人手工編寫與審計，並附帶完整註釋，以確保每一條攔截規則都公開、真實、可控、無污染。

## 自動化更新

Aegis 採用 [GitHub](https://github.com) 托管實現自動更新機制，確保資料始終處於最新狀態，支援 Surge 遠端訂閱使用。

若未啟用設定變更自動重載功能，亦可手動重新整理外部資源或重新載入設定，以確保規則集保持最新狀態。

## Surge IPv4 設定連結

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/config/Aegis_CN.conf

Aegis (TC): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/config/Aegis_TC.conf

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/config/Aegis_EN.conf

## Surge IPv6 設定連結

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/config/Aegis_IPv6_CN.conf

Aegis (TC): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/config/Aegis_IPv6_TC.conf

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/config/Aegis_IPv6_EN.conf

## 規則模組

- 請參閱 [Aegis Wiki 規則模組](https://github.com/Thoseyearsbrian/Aegis/wiki/規則模組)

## 路由策略

- 請參閱 [Aegis Wiki 路由策略](https://github.com/Thoseyearsbrian/Aegis/wiki/路由策略)

## 快速開始

- 請參閱 [Aegis Wiki 快速開始](https://github.com/Thoseyearsbrian/Aegis/wiki/快速開始)

## 注意事項

- 請參閱 [Aegis Wiki 注意事項](https://github.com/Thoseyearsbrian/Aegis/wiki/注意事項)

## 特別致謝

- 請參閱 [Aegis Wiki 特別致謝](https://github.com/Thoseyearsbrian/Aegis/wiki/特別致謝)

## 免責聲明

- 請參閱 [Aegis Wiki 免責聲明](https://github.com/Thoseyearsbrian/Aegis/wiki/免責聲明)

## 版權聲明

- 請參閱 [Aegis Wiki 版權聲明](https://github.com/Thoseyearsbrian/Aegis/wiki/版權聲明)

## 社群支援

- [Telegram 頻道](https://t.me/AegisUpdates)：用於發布 Aegis 專案更新、規則維護說明與重要通知。
- [Telegram 群組](https://t.me/aegisdiscussion)：錯誤報告：回報 Aegis 相關問題。