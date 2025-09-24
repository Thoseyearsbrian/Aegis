<h1 align="center">SurgeAegis - Surge个人数字防火墙规则集</h1>

<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/Icons/Groups/surge-config-import-step-1.png" width="300">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/Icons/Groups/surge-config-import-step-2.png" width="300">
</p>

## 项目特点

1. **安全架构全覆盖**  
专注网络防御与隐私保护，主动封锁 APT 源、DNS 污染、恶意追踪等高危流量。

2. **规则体系层级化**  
规则精细分层，覆盖 Pegasus、僵尸网络、远控木马等威胁，支持按需调用。

3. **注释完整可审计**  
所有规则附带来源、分类与用途说明，便于溯源、校对与长期维护。

4. **配置链接全自控**  
规则与配置托管于私有 GitHub 仓库，无外部依赖或第三方跳转。

5. **策略分组精细化**  
内置多个策略组（如 Google / OpenAI），支持容灾、分流与协议区分。

6. **环境纯净无暗链**  
配置无预置劫持、无隐性分流、无灰色行为，保障系统稳定透明。

7. **更新机制双通道**  
支持 GitHub / Telegram 双通道更新同步，保障规则实时与透明性。

8. **专业用户可拓展**  
支持高级用户自定义规则、策略组管理与集成至多平台防火墙环境。

## 项目优势

支持高级用户自定义规则、策略组管理与集成多平台防火墙环境。

Aegis 项目聚焦以下关键网络威胁场景的识别与封锁：

- APT 攻击组织 的 C2 控制节点与伪装基础设施  
- 监听类 SDK 的指纹域名、回传 API、可疑 CDN 分发节点  
- DNS 污染 / 劫持 / 注入 行为所关联的域名与伪装 IP  
- 僵尸网络 / 远控木马 / RAT 等远程控制信道与命令下发节点  
- 广告平台与追踪系统 所使用的跟踪域名、行为识别脚本服务

本项目力求构建可审计、可定制、可扩展的规则体系，  涵盖主流攻击手法与监控机制，为用户提供主动防御能力。

## 如何使用

### 1. 安装环境

**最低需要iOS 18 / macOS 15系统，否则可能会有兼容问题**

Surge最低支持版本 :

>**App Store 版 5.13.0（3310） 或更新版本**
>
>**macOS 版 5.8.1（2929） 或更新版本**
### 2. 配置文件链接

**适合 Surge 5 卡片视图**

> **完整版（英文）:** [点击下载](https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_EN.conf) 

> **完整版（中文）:** [点击下载](https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_CN.conf)

### 3. 使用方式

复制配置链接 -> 打开 Surge -> 从URL下载配置 -> 粘贴链接 -> 在文本模式中编辑 -> 修改“外部节点”的对应参数 -> 完成!

<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/Icons/Groups/surge-config-import-guide-step-by-step.png" width="600"></img>
</p>

## 注意事項

1. 一定要仔细阅读使用方式！
2. 一定要仔细阅读使用方式！
3. 一定要仔细阅读使用方式！

