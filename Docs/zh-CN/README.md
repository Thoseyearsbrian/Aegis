<!-- Aegis Logo -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/Aegis_Cover_Image.png" alt="Aegis Cover Image"/>
</p>

<h1 align="center">Aegis — Surge 个人数字防火墙规则集</h1>
<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-1.png" width="300"></img>
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-2.png" width="300"></img>
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
  <a href="https://github.com/Thoseyearsbrian/Aegis/blob/main/Docs/en-US/README.md"><b>【English Documentation Here】</b></a>
</p>

## 项目概述

[Aegis](https://github.com/Thoseyearsbrian/Aegis) 专用的网络安全规则集，专注于识别应用层与传输层的潜在通信威胁，涵盖 [DNS污染](https://zh.wikipedia.org/wiki/域名服务器缓存污染)、[APT 攻击源](https://zh.wikipedia.org/wiki/高级长期威胁)、[SDK回传监听](https://en.wikipedia.org/wiki/Software_development_kit)、[后门通信](https://en.wikipedia.org/wiki/Back_door)、[PCDN 链路通信](https://en.wikipedia.org/wiki/P2P_caching)、[C2 控制器](https://zh.wikipedia.org/wiki/殭屍網絡)等潜在通信行为，同时扩展对全球主流广告、行为追踪与成人内容平台的域名识别，帮助用户在 iOS / macOS 本地实现流量的精准识别与分类，并根据自身需求自主设定流量策略。

同时，项目已收录多个全球高风险攻击源的规则集，其中包括飞马间谍软件（[Pegasus](https://en.wikipedia.org/wiki/Pegasus_(spyware))）的相关通信基础设施与行为特征识别策略。

本项目全面采用加密 DNS，拒绝明文请求，确保通信加密与隐私安全。即便在如 iPhone 等缺乏传统安全软件支持的设备上，亦可提供流量层级的有效防护。

## 项目优势

Aegis 规则集致力于识别与分类以下高风险通信行为：

- 广告域名识别、行为监控与监听型 CDN节点
- PCDN 链路中继与共享带宽通信行为
- 僵尸网络、远控后门与恶意控制器
- SDK 行为指纹与回传监听域名
- APT 攻击组织的 C2 基础设施
- DNS 污染 / 劫持 / 注入行为

Aegis 专为 Surge 平台设计，全面兼容 iOS 与 macOS 系统，具备良好的可读性、可审计性与模块化部署能力，适用于策略分流、通信识别与安全辅助配置等多种应用场景。

此外，Aegis 还额外提供一个可选启用的高级模块 — CA_Block.list，用于拦截全球范围内存在安全争议或曾被公开吊销的 CA根证书、OCSP接口与吊销列表（CRL）域名。该模块适用于有更高数字信任要求的用户，可进一步减少中间人攻击与恶意证书链的潜在风险。

## 项目理念

Aegis 是一个坚持技术中立、信息透明、独立自主的安全规则项目。  我坚信每个人都应拥有对其网络流量的知情权与控制权。因此，Aegis 不接受任何形式的商业投资或资本控制，为保持纯粹的独立性与安全可信性，所有配置文件完全由本人手工编写与审计，并附带完整注释，以确保每一条拦截规则都公开、真实、可控、无污染。

## Aegis 主规则模块列表

| 模块编号 | 模块名称 | 文件名 | 模块说明 | 判定标准 |
| :------: | :------: | :------------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ① | 不受信任的证书机构 | CA_Block.list | 标记存在滥发或吊销记录的 CA 根证书、OCSP 接口与吊销列表（CRL）域名，适用于强化数字信任链场景（高级模块-默认不启用） | 存在证书滥发、伪造签发或被吊销的行为记录 |
| ② | 广告域名识别 | AdDomain.list | 涵盖商业广告投放、社交像素追踪、行为分析与第三方统计 SDK 等域名识别（识别模块-默认不启用） | 依据投放行为特征与数据收集模式进行识别，区分于遥测监听类通信 |
| ③ | 成人内容识别 | AdultDomain.list | 涵盖全球主流成人平台相关域名识别（识别模块-默认不启用） | 与成人内容传播直接关联的域名 |
| ④ | PCDN 通信识别 | PCDNDomain.list | 疑似“共享带宽”架构的链路通信行为，涉及设备转发、缓存中继与分布式分发节点识别（识别模块-默认不启用） | 依据通信路径与节点分布模式，涉及多级链路的中继、缓存与转发特征 |
| ⑤ | 监听与节点识别 | InspectionDomain.list | 链路层或出口级别的主动干预行为，包括 DPI 探测、DNS 污染、HTTP 注入与中间人监听等识别（识别模块-默认不启用） | 依据通信异常特征识别流量篡改、重定向与注入行为，常见于链路干预环境 |
| ⑥ | 行为分析 / 遥测节点识别 | BehaviorDomain.list | 具备行为指纹特征的云服务节点，包含遥测 SDK、分析平台及行为建模服务。依据 DNS 模式、TLS 握手、CDN 请求等特征识别（识别模块-默认不启用） | 聚焦行为分析型 SDK 的通信特征，依据 DNS/TLS 报文与行为模式判断识别，排除广告类与后台上传类 SDK。|
| ⑦ | 后台回连与静默通信节点拦截 | Background_Block.list | 识别 IoT、NAS 或 SDK 中具备配置上传、设备回连等特征的域名，协助识别监听类静默通信（默认启用） | 聚焦监听型 SDK 的后台连接行为，依据通信频率、回连路径与数据上传特征识别，排除广告与行为建模类 SDK。|
| ⑧ | 后门控制与植入通信节点拦截 | Backdoor_Block.list | 默认拦截具有远控、反连、心跳等恶意特征的通信行为，如 RAT、Sliver、Metasploit 等基础设施（默认启用） | 明确具备恶意通信模式或与植入攻击行为直接关联 |
| ⑨ | 僵尸网络与控制节点拦截 | Botnet_Block.list | 默认拦截已知 Botnet 控制源、DDoS 节点、批量控制基础设施等通信路径（默认启用） | 来源于公开报告，具备明确归属与可验证情报链 |
| ⑩ | APT 攻击源拦截 | APT_Block.list | 默认拦截已知 APT 攻击组织的 C2 基础设施，附带归属国编号与 IOC 来源（默认启用） | 来源于公开报告，具备明确归属与可验证情报链 |
| ⑪ | Pegasus 间谍软件通信节点拦截 | Pegasus_Block.list | 收录 Amnesty 公布的 Pegasus 控制器与命令节点，用于识别极高风险监听通信（默认启用） | 基于 Amnesty 公开披露的 Pegasus 控制节点，具监听风险 |

## 自动化更新

Aegis 采用 [GitHub](https://github.com) 托管实现自动更新机制，确保数据始终处于最新状态，支持 Surge 远程订阅使用。

若未启用配置变更自动重载功能，亦可手动刷新外部资源或重新载入配置，以确保规则集保持最新状态。

### 版本说明

Aegis 遵循 [语义化版本](https://semver.org/lang/zh-CN/) 控制规范：vMAJOR.MINOR.PATCH  示例：Aegis v3.0.1,MAJOR=3、MINOR=0、PATCH=1

MAJOR（X）版本（重大更新）: 涉及结构调整 / 兼容性变化  👉 必须重新下载配置，并重新添加节点

MINOR（Y）版本（新增功能）: 新增策略组 / 新模块 / 新能力  👉 建议重新下载配置，并重新添加节点

PATCH（Z）版本（修复更新）: 修复规则 / 注释补全 / 小幅优化  👉 不用重新下载配置，只需更新外部资源即可

💡 建议勾选「当配置从外部程序或远端修改后自动重新载入」以确保 PATCH 版本自动生效。

## Surge IPv4 配置链接

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_CN.conf  

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_EN.conf

## Surge IPv6 配置链接

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_CN.conf  

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_EN.conf

 💡 配置说明：请根据网络环境选择对应配置,如您的网络环境原生支持 IPv6，请使用 IPv6 配置；否则请使用 IPv4 配置。禁止混用，否则将导致请求异常或 DNS 解析失败。

## 配置方式

复制配置链接 -> 打开 Surge -> 从URL下载配置 -> 粘贴链接 -> 在文本模式中编辑 -> 修改“你的节点”至对应参数 -> 完成!

<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step.png" width="600">
</p>

### 视频教程

零基础 Surge 教程 · macOS（4K）｜点击封面跳转观看

[![零基础 Surge 教程 · macOS（4K）](https://img.youtube.com/vi/ano6ysBlD5s/maxresdefault.jpg)](https://youtu.be/ano6ysBlD5s)

## ⚠️ 注意事项

1. **务必启用规则模式（Rule Mode），否则 Aegis 规则集可能无法执行任何防护、分流或拦截机制**

   ```bash
   Aegis 是一套基于规则模式构建的个人数字防火墙体系，依赖 Surge 的规则匹配机制进行域名分类、策略分流与恶意拦截。

   仅在启用规则模式（Rule Mode）时，Aegis 才能实现完整功能。若使用“全局模式”或“直连模式”，虽然仍可按策略访问外部网络，但将跳过全部规则匹配流程，导致以下风险：

   • 域名与 IP 无法被识别分类  
   • 所有拦截机制与模块策略失效  
   • 无法发挥分流、防护、去广告等核心能力

   如遇某些域名因规则匹配失败而暂时无法访问，可**临时切换为“全局模式”或“直连模式”**应急处理。同时，强烈建议在第一时间提交 Issue，我们将尽快补充至对应规则集中，以确保下次访问无需绕行。
   ```

2. **推荐将`China.list`（域名）与 `GEOIP,CN`（IP段）规则组合使用，以提高对中国流量的匹配准确性：**

   ```bash
   RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/rules/China.list, DIRECT   # 精确匹配中国域名
   GEOIP,CN,DIRECT                                                                                  # 匹配未在域名规则中出现的中国大陆 IP
   FINAL,REJECT                                                                                     # 最终默认拒绝规则（请勿将 GEOIP 放于其后）
   ```

3. **支持使用非中国大陆国家的 GEOIP 查询规则，因为目前使用的数据库支持全球国家IP段**

   ```bash
   GEOIP,US, PROXY   # 正确
   GEOIP,AU, PROXY   # 正确
   GEOIP,CN, DIRECT  # 正确
   ```
4. **出现 “tun-excluded-routes 参数已配置，该参数可能导致切换网络后出现异常，请谨慎使用” 的说明**

   ```bash
   该提示并非错误或冲突，而是 Surge 的系统级提醒。在固定网络环境下，此提示可安全忽略。
   若切换网络（如 Wi-Fi ↔ 热点）后出现 AirDrop、Bonjour、NAS 等局域网通信异常，可在菜单中选择「停止代理」→「启动代理」以重建路由表并恢复连接。
   ```


## 🌟 特别致谢

本项目在设计与整理过程中，参考并借鉴了 [GitHub](https://github.com) 社区中众多优秀开源项目，谨向所有为开源社区作出贡献的开发者致以诚挚感谢。

为满足个人网络安全防护需求，本项目在既有规则基础上进行了深度定制与安全优化。为保障项目的完整性、安全性与长期可用性，所有使用的素材与规则均通过本仓库自托管，避免因依赖第三方源而引发的更新失效或信任风险。

### ✍️ 核心框架参考

[@Rabbit-Spec](https://github.com/Rabbit-Spec) 👉 项目整体架构与规则逻辑的主要参考来源，当前版本在此基础上进行了深度重构与安全适配。

[@AmnestyTech](https://github.com/AmnestyTech) 👉  提供 [Pegasus](https://raw.githubusercontent.com/AmnestyTech/investigations/master/2021-07-18_nso/domains.txt) 相关 IOC 数据，作为规则构建的重要信息源([CC BY 2.0 License](https://creativecommons.org/licenses/by/2.0/))。

[@ESET](https://github.com/eset) 👉 提供 [malware-ioc](https://github.com/eset/malware-ioc) 公共仓库数据，作为 APT 相关规则的重要信息源([BSD 2‑Clause License](https://github.com/eset/malware-ioc/blob/master/LICENSE))。

### 🎖️ 重要贡献者

[@mieqq](https://github.com/mieqq) 👉 Surge 中文社区的重要推动者，其仓库 [mieqq](https://github.com/mieqq/mieqq) 长期维护多种规则与模块,对早期生态建设与推广使用做出突出贡献。

以上引用内容排名不分先后，若有遗漏您的项目或贡献，敬请谅解并欢迎联系我，我将第一时间补充致谢。

## 🔐 免责声明

本项目为公益性质的开源安全规则集，旨在帮助用户提升网络安全防护能力，使用本项目即表示您已阅读、理解并同意以下条款：

1. **第三方来源说明**：本项目部分内容参考公开威胁情报（如安全社区报告、威胁数据库、GitHub 项目等），所有相关引用均已注明出处。如有异议，请联系我进行修正或删除。
2. **识别模块启用声明**：本项目坚持技术中立与信息透明的原则，规则集旨在辅助用户识别潜在风险通信行为。所有识别模块默认不启用,相关策略制定与启用完全由用户自主决定，项目作者不对因用户配置所导致的通信风险承担任何责任。
3. **误杀风险提示**：鉴于规则集中可能涉及通用封锁策略，使用者应在部署前充分测试，确保不影响正常业务。如因误拦截造成连接异常、功能缺失或其他后果，项目作者不承担任何责任。
4. **商业用途说明**：本项目本项目以 [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE) 协议开源发布，您可以自由用于商业与非商业目的，但请务必遵守许可证条款，保留原始作者署名与注释说明。我们反对滥用规则集用于闭源、侵害公共利益或违背开源精神的商业行为。
5. **无担保条款**：本项目以“按现状”形式提供，不对其完整性、准确性、实时性或适配性做出任何明示或暗示的担保。使用者应自行判断适用性并承担所有使用风险。
6. **用途限定**：所有规则与配置文件仅供用于合法的网络防御、流量识别与安全研究。严禁将本项目用于任何攻击性行为、逆向工程、绕过审计等违法或灰色用途。
7. **责任限制**：对因使用、复制或传播本项目内容所产生的任何直接或间接损失（包括但不限于数据泄漏、业务中断、安全故障等），项目作者不承担任何法律责任。
8. **变更权利**：项目作者保留随时更新、修改或删除项目内容与本免责声明的权利，恕不另行通知。建议您定期检查仓库以获取最新版本。

**本人郑重声明**：本项目不作恶、不夹带私货，不推荐任何代理节点部署、不涉及流量劫持或监听机制，亦不包含任何恶意逻辑或隐藏行为。所有规则内容均以明文形式提供，结构清晰、注释完整、不依赖第三方源，所有规则文件均托管于本仓库，便于社区成员审阅、溯源与监督。

## 🏅 版权声明

**版权与分发**：本项目采用 [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE) 授权。你可以自由使用、修改与分发本项目内容，包括用于商业用途。

我们鼓励你遵循开源精神：

- **保留原始作者署名及完整许可证内容；**
- **不得删除或隐藏源代码注释与协议声明**；
- **不滥用规则集用于闭源或侵犯公共利益的行为。**

此外，Aegis 项目已启用 [GPG](https://gnupg.org) 签名（Git Commit Signing）机制，以确保项目代码来源真实可信、未被篡改。你可通过 GPG 签名验证每一次提交操作的完整性，从而获得更高的安全保障。

## 🙌  社区支持

如果你认可本项目的价值，欢迎 Star ⭐️ 支持，相关更新将同步发布至 [Telegram](https://telegram.org) 通知频道，欢迎订阅关注。

**Telegram 版本更新频道** - <a href="https://t.me/aegisupdates" target="_blank">Aegis Updates</a> : 用于发布最新版本、更新日志与重要公告

**Telegram 用户共建群组** - <a href="https://t.me/aegisdiscussion" target="_blank">Aegis Discussion</a> : 欢迎提交建议、反馈问题、参与社区共建