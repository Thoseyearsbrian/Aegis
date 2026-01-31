<!-- Aegis Logo -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/Aegis_Cover_Image.png" alt="Aegis Cover Image"/>
</p>

<h1 align="center">Aegis — Surge 個人數位防火牆規則集</h1>
<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-tc-1.png" width="300" alt="Surge iOS：Aegis_TC 配置概覽介面截圖" />
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-tc-2.png" width="300" alt="Surge iOS：Aegis_TC 策略群組介面截圖" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License: Apache 2.0" />
  <img src="https://github.com/Thoseyearsbrian/GeoIP2-CN/actions/workflows/update.yml/badge.svg" alt="GeoIP Auto Update Status" />
  <img src="https://img.shields.io/github/stars/Thoseyearsbrian/Aegis?style=social" alt="GitHub stars" />
  <img src="https://img.shields.io/github/v/release/Thoseyearsbrian/Aegis?include_prereleases&label=version" alt="Version" />
  <img src="https://img.shields.io/github/last-commit/Thoseyearsbrian/Aegis" alt="Last Commit" />
  <a href="https://github.com/Thoseyearsbrian/Aegis">
    <img src="https://img.shields.io/badge/Mirror--Prohibited-red" alt="Mirror Prohibited" />
  </a>
</p>

<p align="center">
  <a
    href="https://github.com/Thoseyearsbrian/Aegis/blob/main/Docs/en-US/README.md"
    title="View Aegis Documentation in English"
    aria-label="English Documentation for Aegis project"
  >
    <b>【English Documentation Here】</b>
  </a>
</p>

## 專案概述

[Surge](https://nssurge.com) 個人數位防火牆規則集，專注於識別應用層與傳輸層的潛在通訊威脅，涵蓋 [DNS污染](https://zh.wikipedia.org/wiki/域名服务器缓存污染)、[APT 攻擊源](https://zh.wikipedia.org/wiki/高级长期威胁)、[SDK回傳監聽](https://en.wikipedia.org/wiki/Software_development_kit)、[後門通訊](https://en.wikipedia.org/wiki/Back_door)、[PCDN 鏈路通訊](https://en.wikipedia.org/wiki/P2P_caching)、[C2 控制器](https://zh.wikipedia.org/wiki/殭屍網絡)等潛在通訊行為，同時擴展對全球主流廣告、行為追蹤與成人內容平台的域名識別，幫助使用者在 iOS 與 macOS 本地實現流量的精準識別與分類，並根據自身需求自主設定流量策略。

同時，專案已收錄多個全球高風險攻擊源的規則集，其中包括飛馬間諜軟體（[Pegasus](https://en.wikipedia.org/wiki/Pegasus_(spyware))）的相關通訊基礎設施與行為特徵識別策略。

本專案全面採用加密 DNS，拒絕明文請求，確保通訊加密與隱私安全。即便在如 iPhone 等缺乏傳統安全軟體支援的裝置上，亦可提供流量層級的有效防護。

## 專案優勢

Aegis 規則集致力於識別與分類以下高風險通訊行為：

- 廣告域名識別、行為監控與監聽型 CDN節點
- PCDN 鏈路中繼與共享頻寬通訊行為
- 殭屍網路、遠控後門與惡意控制器
- SDK 行為指紋與回傳監聽域名
- APT 攻擊組織的 C2 基礎設施
- DNS 污染 / 劫持 / 注入行為

Aegis 專為 Surge 平台設計，全面相容 iOS 與 macOS 系統，具備良好的可讀性、可審計性與模組化部署能力，適用於策略分流、通訊識別與安全輔助設定等多種應用場景。

此外，Aegis 還額外提供一個可選啟用的高級模組 — CA_Block.list，用於攔截全球範圍內存在安全爭議或曾被公開吊銷的 CA根證書、OCSP介面與吊銷列表（CRL）域名。該模組適用於有更高數位信任要求的使用者，可進一步減少中間人攻擊與惡意證書鏈的潛在風險。

## 專案理念

Aegis 是一個堅持技術中立、資訊透明、獨立自主的安全規則專案。  我堅信每個人都應擁有對其網路流量的知情權與控制權。因此，Aegis 不接受任何形式的商業投資或資本控制，為保持純粹的獨立性與安全可信性，所有設定檔完全由本人手工編寫與審計，並附帶完整註釋，以確保每一條攔截規則都公開、真實、可控、無污染。

## Aegis 主規則模組列表

| 模組編號 | 模組名稱 | 檔案名 | 模組說明 | 判定標準 |
| :------: | :------: | :------------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ① | 不受信任的證書機構 | CA_Block.list | 標記存在濫發或吊銷記錄的 CA 根證書、OCSP 介面與吊銷列表（CRL）域名，適用於強化數位信任鏈場景（高級模組-預設不啟用） | 存在證書濫發、偽造簽發或被吊銷的行為記錄 |
| ② | 廣告域名識別 | AdDomain.list | 涵蓋商業廣告投放、社交像素追蹤、行為分析與第三方統計 SDK 等域名識別（識別模組-預設不啟用） | 依據投放行為特徵與資料收集模式進行識別，區分於遙測監聽類通訊 |
| ③ | 成人內容識別 | AdultDomain.list | 涵蓋全球主流成人平台相關域名識別（識別模組-預設不啟用） | 與成人內容傳播直接關聯的域名 |
| ④ | PCDN 通訊識別 | PCDNDomain.list | 疑似“共享頻寬”架構的鏈路通訊行為，涉及裝置轉發、快取中繼與分散式分發節點識別（識別模組-預設不啟用） | 依據通訊路徑與節點分布模式，涉及多級鏈路的中繼、快取與轉發特徵 |
| ⑤ | 監聽與節點識別 | InspectionDomain.list | 鏈路層或出口級別的主動干預行為，包括 DPI 探測、DNS 污染、HTTP 注入與中間人監聽等識別（識別模組-預設不啟用） | 依據通訊異常特徵識別流量竄改、重定向與注入行為，常見於鏈路干預環境 |
| ⑥ | 行為分析 / 遙測節點識別 | BehaviorDomain.list | 具備行為指紋特徵的雲服務節點，包含遙測 SDK、分析平台及行為建模服務。依據 DNS 模式、TLS 握手、CDN 請求等特徵識別（識別模組-預設不啟用） | 聚焦行為分析型 SDK 的通訊特徵，依據 DNS/TLS 報文與行為模式判斷識別，排除廣告類與背景上傳類 SDK。|
| ⑦ | 背景回連與靜默通訊節點攔截 | Background_Block.list | 識別 IoT、NAS 或 SDK 中具備設定上傳、裝置回連等特徵的域名，協助識別監聽類靜默通訊（拦截模組-預設啟用） | 聚焦監聽型 SDK 的背景連線行為，依據通訊頻率、回連路徑與資料上傳特徵識別，排除廣告與行為建模類 SDK。|
| ⑧ | 後門控制與植入通訊節點攔截 | Backdoor_Block.list | 預設攔截具有遠控、反連、心跳等惡意特徵的通訊行為，如 RAT、Sliver、Metasploit 等基礎設施（拦截模組-預設啟用） | 明確具備惡意通訊模式或與植入攻擊行為直接關聯 |
| ⑨ | 殭屍網路與控制節點攔截 | Botnet_Block.list | 預設攔截已知 Botnet 控制源、DDoS 節點、批量控制基礎設施等通訊路徑（拦截模組-預設啟用） | 來源於公開報告，具備明確歸屬與可驗證情報鏈 |
| ⑩ | APT 攻擊源攔截 | APT_Block.list | 預設攔截已知 APT 攻擊組織的 C2 基礎設施，附帶歸屬國編號與 IOC 來源（拦截模組-預設啟用） | 來源於公開報告，具備明確歸屬與可驗證情報鏈 |
| ⑪ | Pegasus 間諜軟體通訊節點攔截 | Pegasus_Block.list | 收錄 Amnesty 公布的 Pegasus 控制器與命令節點，用於識別極高風險監聽通訊（拦截模組-預設啟用） | 基於 Amnesty 公開披露的 Pegasus 控制節點，具監聽風險 |
| ⑫ | 網路釣魚攔截 | Phishing_Block.list | 預設攔截網路釣魚攻擊相關域名，涵蓋假冒登入頁面、偽裝官網、釣魚郵件連結等典型社會工程攻擊行為（拦截模組-預設啟用） | 來源於公開報告，具備明確歸屬與可驗證情報鏈 |
| ⑬ | 網路詐騙攔截 | Scam_Block.list | 預設攔截聲譽極低、存在詐騙、虛假服務或使用者舉報的可疑網站域名（拦截模組-預設啟用） | 來源於公開報告，具備明確歸屬與可驗證情報鏈 |
| ⑭ | 風險通訊觀察列表 | Quarantine_Block.list | 用於納入尚未確認惡意、但具備異常通訊特徵的域名與 IP，涵蓋用途不透明或使用非公開協議、非常規埠的通訊行為，並採取防禦性阻斷策略以降低潛在風險（觀察模組-預設啟用）| 基於異常通訊行為特徵識別，風險尚未完全確認，採取隔離觀察策略以便後續分析與校驗 |

## 自動化更新

Aegis 採用 [GitHub](https://github.com) 托管實現自動更新機制，確保資料始終處於最新狀態，支援 Surge 遠端訂閱使用。

若未啟用設定變更自動重載功能，亦可手動重新整理外部資源或重新載入設定，以確保規則集保持最新狀態。

### 版本說明

Aegis 遵循 [語意化版本](https://semver.org/lang/zh-CN/) 控制規範：vMAJOR.MINOR.PATCH  示例：Aegis v3.0.1,MAJOR=3、MINOR=0、PATCH=1

MAJOR（X）版本（重大更新）: 涉及結構調整 / 相容性變化  👉 必須重新下載設定，並重新添加節點

MINOR（Y）版本（新增功能）: 新增策略組 / 新模組 / 新能力  👉 建議重新下載設定，並重新添加節點

PATCH（Z）版本（修復更新）: 修復規則 / 註釋補全 / 小幅優化  👉 不用重新下載設定，只需更新外部資源即可

💡 建議勾選「當設定從外部程式或遠端修改後自動重新載入」,該選項僅用於設定檔（.conf）變更後的自動加載，PATCH 版本更新仍需手動重新整理外部資源（RULE-SET）後生效。

示例：

當前版本是Aegis v2.0.0,上一版本是Aegis v1.2.4此次就是MAJOR更新(MAJOR=2),必須重新下載設定，並重新添加節點,會自動更新外部資源

當前版本是Aegis v3.3.0,上一版本是Aegis v3.2.2此次就是MINOR更新(MINOR=3),建議重新下載設定，並重新添加節點,會自動更新外部資源

當前版本是Aegis v3.3.4,上一版本是Aegis v3.3.3此次就是PATCH更新(PATCH=4),不用重新下載設定，只需更新外部資源即可

總結:

只要重新下載設定檔（.conf）,並重新添加節點,就會自動更新外部資源(勾選了「當設定從外部程式或遠端修改後自動重新載入」)。

PATCH 版本更新仍需手動重新整理外部資源（RULE-SET）後才能生效。

## Surge IPv4 設定連結

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_CN.conf

Aegis (TC): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_TC.conf

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_EN.conf

## Surge IPv6 設定連結

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_CN.conf

Aegis (TC): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_TC.conf

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_EN.conf

 💡 設定說明：請根據網路環境選擇對應設定,如您的網路環境原生支援 IPv6，請使用 IPv6 設定；否則請使用 IPv4 設定。禁止混用，否則將導致請求異常或 DNS 解析失敗。

## 設定方式

複製設定連結 -> 打開 Surge -> 從URL下載設定 -> 貼上連結 -> 在文本模式中編輯 -> 修改“你的節點”至對應參數 -> 完成!

<p align="center">
  <img
    src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step-tc.png"
    width="600"
    alt="Surge iOS：Aegis_TC 規則集匯入設定步驟示意圖（繁體中文）"
  >
</p>

### 影片教學

請選擇你所使用的平台，進入對應的影片教學頁面：

零基礎 Surge 教學 · iOS（4K）｜點擊封面跳轉至 YouTube 觀看

<p align="center">
<a href="https://youtu.be/cKhRdQF5FTo">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/beginner-friendly-surge-guide-ios-4k.png"
       alt="零基礎 Surge 教學 · iOS（4K）"
       width="600" />
</a>
</p>

零基礎 Surge 教學 · macOS（4K）｜點擊封面跳轉至 YouTube 觀看

<p align="center">
<a href="https://youtu.be/ano6ysBlD5s">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/beginner-friendly-surge-guide-macos-4k.png"
       alt="零基礎 Surge 教學 · macOS（4K）"
       width="600" />
</a>
</p>

## ⚠️ 注意事項

1. **務必啟用規則模式（Rule Mode），否則 Aegis 規則集可能無法執行任何防護、分流或攔截機制**

   ```bash
   Aegis 是一套基於規則模式構建的個人數位防火牆體系，依賴 Surge 的規則匹配機制進行域名分類、策略分流與惡意攔截。

   僅在啟用規則模式（Rule Mode）時，Aegis 才能實現完整功能。若使用“全局模式”或“直連模式”，雖然仍可按策略訪問外部網路，但將跳過全部規則匹配流程，導致以下風險：

   • 域名與 IP 無法被識別分類  
   • 所有攔截機制與模組策略失效  
   • 無法發揮分流、防護、去廣告等核心能力

   如遇某些域名因規則匹配失敗而暫時無法訪問，可**臨時切換為“全局模式”或“直連模式”**應急處理。同時，強烈建議在第一時間提交 Issue，我們將盡快補充至對應規則集中，以確保下次訪問無需繞行。
   ```

2. **建議將`China.list`（域名）與 `GEOIP,CN`（IP段）規則組合使用，以提高對中國流量的匹配準確性：**

   ```bash
   RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/rules/China.list, DIRECT   # 精確匹配中國域名
   GEOIP,CN,DIRECT                                                                                  # 匹配未在域名規則中出現的中國大陸 IP
   FINAL,REJECT                                                                                     # 最終預設拒絕規則（請勿將 GEOIP 放於其後）
   ```

3. **支援使用非中國大陸國家的 GEOIP 查詢規則，因為目前使用的資料庫支援全球國家IP段**

   ```bash
   GEOIP,US, PROXY   # 正確
   GEOIP,AU, PROXY   # 正確
   GEOIP,CN, DIRECT  # 正確
   ```
4. **出現 “tun-excluded-routes 參數已設定，該參數可能導致切換網路後出現異常，請謹慎使用” 的說明**

   ```bash
   該提示並非錯誤或衝突，而是 Surge 的系統級提醒。在固定網路環境下，此提示可安全忽略。
   若切換網路（如 Wi-Fi ↔ 熱點）後出現 AirDrop、Bonjour、NAS 等區域網通訊異常，可在選單中選擇「停止代理」→「啟動代理」以重建路由表並恢復連線。
   ```


## 🌟 特別致謝

本專案在設計與整理過程中，參考並借鑒了 [GitHub](https://github.com) 社群中眾多優秀開源專案，謹向所有為開源社群作出貢獻的開發者致以誠摯感謝。

為滿足個人網路安全防護需求，本專案在既有規則基礎上進行了深度定制與安全優化。為保障專案的完整性、安全性與長期可用性，所有使用的素材與規則均透過本倉庫自托管，避免因依賴第三方源而引發的更新失效或信任風險。

### ✍️ 核心框架參考

[@Rabbit-Spec](https://github.com/Rabbit-Spec) 👉 專案整體架構與規則邏輯的主要參考來源，當前版本在此基礎上進行了深度重構與安全適配。

[@AmnestyTech](https://github.com/AmnestyTech) 👉  提供 [Pegasus](https://raw.githubusercontent.com/AmnestyTech/investigations/master/2021-07-18_nso/domains.txt) 相關 IOC 資料，作為規則建構的重要資訊源([CC BY 2.0 License](https://creativecommons.org/licenses/by/2.0/))。

[@ESET](https://github.com/eset) 👉 提供 [malware-ioc](https://github.com/eset/malware-ioc) 公共倉庫資料，作為 APT 相關規則的重要資訊源([BSD 2‑Clause License](https://github.com/eset/malware-ioc/blob/master/LICENSE))。

### 🎖️ 重要貢獻者

[@mieqq](https://github.com/mieqq) 👉 Surge 中文社群的重要推動者，其倉庫 [mieqq](https://github.com/mieqq/mieqq) 長期維護多種規則與模組,對早期生態建設與推廣使用做出突出貢獻。

以上引用內容排名不分先後，若有遺漏您的專案或貢獻，敬請諒解並歡迎聯繫我，我將第一時間補充致謝。

## 🔐 免責聲明

本專案為公益性質的開源安全規則集，旨在幫助使用者提升網路安全防護能力，使用本專案即表示您已閱讀、理解並同意以下條款：

1. **第三方來源說明**：本專案部分內容參考公開威脅情報（如安全社群報告、威脅資料庫、GitHub 專案等），所有相關引用均已註明出處。如有異議，請聯繫我進行修正或刪除。
2. **識別模組啟用聲明**：本專案堅持技術中立、資訊透明、獨立自主的原則，規則集旨在輔助使用者識別潛在風險通訊行為。所有識別模組預設不啟用,相關策略制定與啟用完全由使用者自主決定，專案作者不對因使用者設定所導致的通訊風險承擔任何責任。
3. **誤殺風險提示**：鑑於規則集中可能涉及通用封鎖策略，使用者應在部署前充分測試，確保不影響正常業務。如因誤攔截造成連線異常、功能缺失或其他後果，專案作者不承擔任何責任。
4. **商業用途說明**：本專案本專案以 [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE) 協議開源發布，您可以自由用於商業與非商業目的，但請務必遵守許可證條款，保留原始作者署名與註釋說明。我們反對濫用規則集用於閉源、侵害公共利益或違背開源精神的商業行為。
5. **無擔保條款**：本專案以“按現狀”形式提供，不對其完整性、準確性、即時性或適配性做出任何明示或暗示的擔保。使用者應自行判斷適用性並承擔所有使用風險。
6. **用途限定**：所有規則與設定檔僅供用於合法的網路防禦、流量識別與安全研究。嚴禁將本專案用於任何攻擊性行為、逆向工程、繞過審計等違法或灰色用途。
7. **責任限制**：對因使用、複製或傳播本專案內容所產生的任何直接或間接損失（包括但不限於資料外洩、業務中斷、安全故障等），專案作者不承擔任何法律責任。
8. **變更權利**：專案作者保留隨時更新、修改或刪除專案內容與本免責聲明的權利，恕不另行通知。建議您定期檢查倉庫以取得最新版本。

**本人鄭重聲明**：本專案不作惡、不夾帶私貨，不推薦任何代理節點部署、不涉及流量劫持或監聽機制，亦不包含任何惡意邏輯或隱藏行為。所有規則內容均以明文形式提供，結構清晰、註釋完整、不依賴第三方源，所有規則檔案均託管於本倉庫，便於社群成員審閱、溯源與監督。

## 🏅 版權聲明

**版權與分發**：本專案採用 [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE) 授權。你可以自由使用、修改與分發本專案內容，包括用於商業用途。

我們鼓勵你遵循開源精神：

- **保留原始作者署名及完整許可證內容；**
- **不得刪除或隱藏原始碼註釋與協議聲明**；
- **不濫用規則集用於閉源或侵犯公共利益的行為。**

此外，Aegis 專案已啟用 [GPG](https://gnupg.org) 簽名（Git Commit Signing）機制，以確保專案程式碼來源真實可信、未被篡改。你可透過 GPG 簽名驗證每一次提交操作的完整性，從而獲得更高的安全保障。

## 🙌  社群支援

如果你認可本專案的價值，歡迎 Star ⭐️ 支援，相關中文更新說明將同步發布至 [Telegram](https://telegram.org) 通知頻道，歡迎訂閱關注。

**Telegram 版本更新頻道** - <a href="https://t.me/aegisupdates" target="_blank">Aegis Updates</a> : 用於發布最新版本、更新日誌與重要公告