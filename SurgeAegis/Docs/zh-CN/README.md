<h1 align="center">Aegis — Surge 个人数字防火墙规则集</h1>
<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-1.png" width="300"></img>
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-2.png" width="300"></img>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License" />
  <img src="https://github.com/Thoseyearsbrian/GeoIP2-CN/actions/workflows/update.yml/badge.svg" alt="GeoIP Auto Update Status" />
  <img src="https://img.shields.io/github/stars/Thoseyearsbrian/Aegis?style=social" alt="GitHub stars" />
  <img src="https://img.shields.io/github/v/release/Thoseyearsbrian/Aegis?include_prereleases&label=version" alt="Version" />
  <img src="https://img.shields.io/github/last-commit/Thoseyearsbrian/Aegis" alt="Last Commit" />
</p>

<p align="center">
  <a href="https://github.com/Thoseyearsbrian/Aegis"><b>【English Documentation Here】</b></a>
</p>

A high-performance, cross-platform rule repository focused on network-layer defense. Designed for Surge, Clash, QuantumultX and OpenWrt. Protects against APT threats, DNS poisoning, malicious C2 traffic, SDK telemetry, and botnet sources. Supports iOS, macOS, Windows, Android, and router platforms.

## 项目背景

[Aegis](https://github.com/Thoseyearsbrian/Aegis)是一个完全由个人维护的网络安全规则集，专注于应对现代网络层威胁，旨在帮助全球用户构建本地化的网络防御体系。项目通过封锁DNS 污染、APT 攻击源、SDK回传监听、后门域名、C2 控制器等潜在通信行为，并进一步扩展至全球主流广告与追踪域名的拦截，实现本地流量精准识别与高效阻断。同时，项目已收录多个全球高风险攻击源的规则集，其中包括 Pegasus（飞马）间谍软件的相关通信基础设施与行为特征识别策略。

本项目全面采用加密 DNS，拒绝明文请求，确保通信加密与隐私安全。即便在如 iPhone 等缺乏传统安全软件支持的设备上，亦可提供流量层级的有效防护。

此外，Aegis 还额外提供一个可选启用的高级模块 — CA_Block.list，用于拦截全球范围内存在安全争议或曾被公开吊销的 CA 根证书、OCSP 接口与吊销列表（CRL）域名。该模块适用于有更高数字信任要求的用户，可进一步减少中间人攻击与恶意证书链的潜在风险。

## 项目优势

Aegis 规则集致力于识别与拦截以下高风险通信行为：

- APT 攻击组织的 C2 基础设施
- SDK 行为指纹与回传监听域名
- DNS 污染 / 劫持 / 注入行为
- 僵尸网络、远控后门与恶意控制器
- 广告追踪、行为监控与监听型 CDN节点

Aegis 支持主流平台如 **Surge、Clash、QuantumultX、OpenWrt**，兼容 iOS、macOS、Windows、Android 等多系统环境，具备良好的可读性、可审计性与模块化部署能力，适用于策略分流、防火墙辅助配置等多种应用场景。你还可以按需启用高级模块 CA_Block.list，用于屏蔽高风险 CA 根证书验证行为，从而进一步强化中间人攻击的防御能力。

## 项目理念

Aegis 是一个坚持技术中立、信息透明、自主独立的安全规则项目。  我坚信每个人都应拥有对其网络流量的知情权与控制权。因此，Aegis 不接受任何形式的商业投资或资本控制，为保持纯粹的独立性与安全可信性，所有配置文件完全由本人手工编写与审计，并附带完整注释，以确保每一条拦截规则都公开、真实、可控、无污染。

## 自动化更新

Aegis 采用 GitHub 托管实现自动更新机制，确保数据始终处于最新状态，支持 Surge、Clash 、QuantumultX等工具远程订阅使用。

## 配置链接

SurgeAegis（CN）：https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_CN.conf  
SurgeAegis（EN）：https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_EN.conf  

## 配置方式

复制配置链接 -> 打开 Surge -> 从URL下载配置 -> 粘贴链接 -> 在文本模式中编辑 -> 修改“你的节点”至对应参数 -> 完成!

<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step.png" width="600">
</p>


## ⚠️ 注意事项

1. **禁用或删除** 与 **中国大陆 IP 地址段** 相关的规则或规则集

   ``` bash
   RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/rules/China.list, DIRECT # 禁用或删除类似规则
   GEOIP,CN,DIRECT # 与上一条类似的规则与本条规则不可共存
   ```

2.  GEOIP-CN 查询规则建议**紧随最终规则之上**，以避免域名规则被忽略导致判断错误。

    ``` bash
    # ... 省略其他规则 ...
    GEOIP,CN,DIRECT # 建议在这里使用规则
    FINAL,REJECT # 最终规则
    ```

3. 规则中**不可以**存在其他国家或地区的 `GEOIP` 查询规则，因为项目提供的数据库中**仅包含中国大陆地区的 IP 地址段记录**

   ``` bash
   GEOIP, US, PROXY # 错误，无法查询到相关记录
   GEOIP, AU, PROXY # 错误，无法查询到相关记录
   GEOIP, HK, PROXY # 错误，无法查询到相关记录
   GEOIP, CN, DIRECT # 正确
   ```

## 🌟 特别致谢

本项目在设计与整理过程中，参考并借鉴了 GitHub 社区中众多优秀开源项目，谨向所有为开源社区作出贡献的开发者致以诚挚感谢。

为满足个人网络安全防护需求，本项目在既有规则基础上进行了深度定制与安全优化。为保障项目的完整性、安全性与长期可用性，所有使用的素材与规则均通过本仓库自托管，避免因依赖第三方源而引发的更新失效或信任风险。

### **核心框架参考**

[@Rabbit-Spec](https://github.com/Rabbit-Spec) 👉 项目整体架构与规则逻辑的主要参考来源，当前版本在此基础上进行了深度重构与安全适配。

### **脚本 / 规则来源参考**

[@Nebulosa-Cat](https://github.com/Nebulosa-Cat)

[@NobyDa](https://github.com/NobyDa)

[@LucaLin233](https://github.com/LucaLin233)

[@Hyseen](https://github.com/Hyseen)

[@congcong0806](https://github.com/congcong0806)

[@fishingworld](https://github.com/fishingworld)

[@mieqq](https://github.com/mieqq)

[@TributePaulWalker](https://github.com/TributePaulWalker)

### **分流/重写规则维护参考**

- [@blackmatrix7](https://github.com/blackmatrix7) 👉  其高质量规则集为部分条目构建与优化提供了参考基础。

### **Apple 服务完整性维护**

- [@VirgilClyne](https://github.com/VirgilClyne) 👉  针对 Apple 服务的解锁与规则适配部分提供了重要思路。

### **Pegasus 间谍软件 IOC 来源**

- [@AmnestyTech](https://github.com/AmnestyTech) 👉  提供 Pegasus 相关 IOC 数据，作为规则构建的重要信息源。

以上引用内容排名不分先后，若有遗漏您的项目或贡献，敬请谅解并欢迎联系我，我将第一时间补充致谢。

## 🔐 免责声明

本项目为公益性质的开源安全规则集，旨在帮助用户提升网络安全防护能力，使用本项目即表示您已阅读、理解并同意以下条款：

1. **第三方来源说明**：本项目部分内容参考公开威胁情报（如安全社区报告、威胁数据库、GitHub 项目等），所有相关引用均已注明出处。如有异议，请联系我进行修正或删除。
2. **误杀风险提示**：鉴于规则集中可能涉及通用封锁策略，使用者应在部署前充分测试，确保不影响正常业务。如因误拦截造成连接异常、功能缺失或其他后果，项目作者不承担任何责任。
3. **商业用途说明**：本项目本项目以 MIT 协议开源发布，您可以自由用于商业与非商业目的，但请务必遵守许可证条款，保留原始作者署名与注释说明。我们反对滥用规则集用于闭源、侵害公共利益或违背开源精神的商业行为。
4. **无担保条款**：本项目以“按现状”形式提供，不对其完整性、准确性、实时性或适配性做出任何明示或暗示的担保。使用者应自行判断适用性并承担所有使用风险。
5. **用途限定**：所有规则与配置文件仅供用于合法的网络防御、流量控制与安全研究。严禁将本项目用于任何攻击性行为、逆向工程、绕过审计等违法或灰色用途。
6. **责任限制**：对因使用、复制或传播本项目内容所产生的任何直接或间接损失（包括但不限于数据泄漏、业务中断、安全故障等），项目作者不承担任何法律责任。
7. **变更权利**：项目作者保留随时更新、修改或删除项目内容与本免责声明的权利，恕不另行通知。建议您定期检查仓库以获取最新版本。

本人郑重声明：本项目不作恶、不夹带私货，不推荐任何代理节点部署、不涉及流量劫持或监听机制，亦不包含任何恶意逻辑或隐藏行为。所有规则内容均以明文形式提供，结构清晰、注释完整、不依赖第三方源，所有规则文件均托管于本仓库，便于社区成员审阅、溯源与监督。

## 🏅 版权声明

**版权与分发**：本项目采用 [MIT License](https://github.com/Thoseyearsbrian/Aegis/main/LICENSE) 授权。你可以自由使用、修改与分发本项目内容，包括用于商业用途。

我们鼓励你遵循开源精神：

- **保留原始作者署名及完整许可证内容；**
- **不得删除或隐藏源代码注释与协议声明**；
- **不滥用规则集用于闭源或侵犯公共利益的行为。**

此外，Aegis 项目已启用 GPG 签名（Git Commit Signing）机制，以确保项目代码来源真实可信、未被篡改。你可通过 GPG 签名验证每一次提交操作的完整性，从而获得更高的安全保障。

建议您基于本项目结构进行维护与扩展，以避免重复开发，节省时间成本，同时获得后续更新与安全优化支持。

## 🙌  社区支持

如果你认可本项目的价值，欢迎 Star ⭐️ 支持，所有规则更新将同步与频道，欢迎订阅关注。

 - [Aegis Updates](https://t.me/AegisUpdates) —— **版本更新通知频道**：用于发布最新规则版本、更新日志与重要公告

 - [Aegis Discussion](https://t.me/+xxxxxxxxx) —— **用户共建交流群**：欢迎提交建议、反馈误杀、参与规则共建

**申请须知**：

为确保协作质量，申请加入共建群时请附上 GitHub 账户链接（仅用于身份验证）。我们欢迎具备真实贡献记录、积极参与开源生态的开发者加入，共同推进规则构建，明确版权归属，并有效防止广告账号、水群等干扰行为。

**群组守则**：

- 本群为纯技术交流平台，严禁发布涉政、涉黄、涉毒、涉枪、涉弹、赌博、诈骗、炒币、广告推销、人身攻击等违法违规或破坏性内容（包括但不限于辱骂、挑衅、刷屏、钓鱼链接等）。一经发现，视情节严重程度立即处理，严重者将被永久封禁。

- 为确保交流安全，请勿上传任何未经检查或来源不明的可执行文件、压缩包、脚本或链接等内容，违者一经查实将予以封禁处理，并纳入黑名单留档。群内所有上传的文件与内容将由 Dr.Web 杀毒机器人等安全工具自动检测与扫描，以防止恶意内容传播。

- 请所有成员自觉维护技术氛围，聚焦网络安全与规则共建，共同营造清朗、有序、互信的社区环境。

- 群组守则适用于所有成员，无任何例外，欢迎大家共同监督与维护。 
