<h1 align="center">Aegis — Personal Firewall Rule Set for Surge</h1>
<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-1.PNG" width="300"></img>
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-2.PNG" width="300"></img>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License" />
  <img src="https://github.com/Thoseyearsbrian/GeoIP2-CN/actions/workflows/update.yml/badge.svg" alt="GeoIP Auto Update Status" />
  <img src="https://img.shields.io/github/stars/Thoseyearsbrian/Aegis?style=social" alt="GitHub stars" />
  <img src="https://img.shields.io/github/v/release/Thoseyearsbrian/Aegis?include_prereleases&label=version" alt="Version" />
  <img src="https://img.shields.io/github/last-commit/Thoseyearsbrian/Aegis" alt="Last Commit" />
</p>

A high-performance, cross-platform rule repository focused on network-layer defense. Designed for Surge, Clash, QuantumultX, and OpenWrt. Protects against APT threats, DNS poisoning, malicious C2 traffic, SDK telemetry, and botnet sources. Supports iOS, macOS, Windows, Android, and router platforms.

## **Project Background**

[Aegis](https://github.com/Thoseyearsbrian/Aegis) is a fully self-maintained, open-source rule set project focused on modern network-layer threats. It helps users worldwide build localized, client-side firewall systems by blocking DNS pollution, APT attack infrastructures, SDK tracking domains, backdoor communications, and malicious C2 servers. It includes rules against global high-risk threats such as Pegasus spyware C2 infrastructure and anomalous behavior patterns.

The project enforces encrypted DNS usage and explicitly blocks plaintext DNS requests to ensure communication security, transparency, and full user-side traffic control. Even on devices such as iPhones, which lack traditional endpoint protection, Aegis provides effective flow-level protection.

Additionally, the project provides an optional high-trust module — CA_Block.list — which blocks controversial or publicly revoked root CAs, OCSP endpoints, and CRL domains worldwide. This is intended for users with high digital trust requirements and helps reduce risks related to man-in-the-middle attacks or malicious certificate chains.

## **Key Features**

Aegis is designed to detect and block the following high-risk communications:

- APT command-and-control (C2) infrastructure
- SDK telemetry and behavioral fingerprinting
- DNS poisoning / injection / hijacking behavior
- Botnets, remote access Trojans, and malware C2 channels
- Ad tracking, behavior analytics, and listening CDNs

It supports **Surge**, **Clash**, **QuantumultX**, **OpenWrt**, and other platforms, and works on iOS, macOS, Windows, Android, and router environments. Rules follow a unified structure with professional annotations, making them readable, auditable, and easy to integrate.You can optionally enable the advanced module CA_Block.list, which blocks high-risk root CA validation behaviors to further strengthen protection against man-in-the-middle (MITM) attacks.

## **Philosophy**

Aegis adheres to technical neutrality, information transparency, and complete independence. I firmly believe every individual has the right to understand and control their network traffic. Therefore, Aegis does **not** accept any form of commercial investment or capital control. To ensure purity, trust, and security, all configurations are handcrafted and audited by me, with complete annotations to guarantee every rule is transparent, verifiable, and pollution-free.

## **Auto Update**

Aegis uses GitHub-based versioning and automation to stay up to date without manual intervention. It supports remote subscription through Surge, Clash, QuantumultX, and other tools.

## **Configuration Links**

SurgeAegis（CN）：https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_CN.conf  
SurgeAegis（EN）：https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_EN.conf  

## **Configuration Guide**

Copy the configuration link → Open Surge → Download from URL → Paste the link → Edit in Text Mode → Replace your node with the correct parameter → Done!

<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step.png" width="600">
</p>

## **⚠️ Notes**

1. **Disable or remove** CN-specific rules such as:

```
RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/rules/China.list,DIRECT
GEOIP,CN,DIRECT
```

2. Place GEOIP,CN rule right before the final rule:

```
GEOIP,CN,DIRECT
FINAL,REJECT
```

3. The GeoIP database only includes **mainland China** IPs. Avoid querying other countries:



```
GEOIP,US,PROXY  # Invalid
GEOIP,HK,PROXY  # Invalid
GEOIP,CN,DIRECT # Valid
```

## **🌟 Special Thanks**

This project is inspired by many outstanding community contributions. Key references include:

- **Project Structure**: 
- [@Rabbit-Spec](https://github.com/Rabbit-Spec) 👉 The primary reference for the overall project architecture and rule logic. The current version has undergone extensive restructuring and security adaptation based on this foundation.
- **Rule Scripts**: 

- [@Nebulosa-Cat](https://github.com/Nebulosa-Cat)

- [@NobyDa](https://github.com/NobyDa)

- [@LucaLin233](https://github.com/LucaLin233)

- [@Hyseen](https://github.com/Hyseen)

- [@congcong0806](https://github.com/congcong0806)

- [@fishingworld](https://github.com/fishingworld)

- [@mieqq](https://github.com/mieqq)

- [@TributePaulWalker](https://github.com/TributePaulWalker)

- **Routing / Rewrite Rules**: 

- [@blackmatrix7](https://github.com/blackmatrix7) 👉 Its high‑quality rule sets have served as a foundational reference for building and optimizing certain entries.

- **Apple Unlock Rules**: 

- [@VirgilClyne](https://github.com/VirgilClyne) 👉 Provided key insights for unlocking Apple services and adapting related rule configurations.

- **Pegasus IOC**: 

- [@AmnestyTech](https://github.com/AmnestyTech)  👉 Provided Pegasus-related IOC data as a critical source for rule construction.

If you believe your work is missing from the acknowledgements, please feel free to contact me — I will add it promptly.

## **🔐 Disclaimer**

This project is a non-profit, open-source security rule set aimed at helping users enhance their network defense capabilities. By using this project, you acknowledge that you have read, understood, and agreed to the following terms:

1. **Third-Party Sources**: Some rules are based on publicly available threat intelligence (e.g., security reports, threat databases, GitHub projects). All references are properly cited. If you believe any content is inappropriate, please contact the author for revision or removal.
2. **False Positive Warning**: As the rule set may include generalized blocking strategies, users must conduct thorough testing before deployment to ensure normal functionality is not impacted. The project author assumes no responsibility for issues caused by false positives, including connection failures or feature disruptions.
3. **Commercial Use Notice**: This project is released under the MIT License. You are free to use it for both commercial and non-commercial purposes, provided that you comply with the license terms and retain proper attribution and annotations. We oppose misuse of the rules for closed-source, anti-public-interest, or anti-open-source practices.
4. **No Warranty**: This project is provided “as is”, without any express or implied warranties regarding its completeness, accuracy, timeliness, or suitability. Users bear full responsibility for any risks incurred from its use.
5. **Usage Restrictions**: All rules and configuration files are strictly intended for legal purposes, including network defense, traffic control, and security research. Any use for offensive actions, reverse engineering, audit evasion, or other illicit activities is strictly prohibited.
6. **Liability Limitation**: The project author shall not be held liable for any direct or indirect losses (including but not limited to data breaches, service interruptions, or security failures) arising from the use, duplication, or distribution of this project.
7. **Right to Modify**: The project author reserves the right to update, modify, or remove any part of this project or disclaimer at any time without prior notice. You are advised to regularly check the repository for the latest version.

Author’s Statement: This project does not engage in malicious activities, does not include hidden backdoors or monitoring mechanisms, does not promote proxy services, and contains no obfuscated or harmful logic. All rule contents are written in plain text, fully commented, structured clearly, and hosted solely within this repository for community review, audit, and traceability.

## **🏅 License**

This project is licensed under the [MIT License](https://github.com/Thoseyearsbrian/Aegis/main/LICENSE). You are free to use, modify, and distribute this project, even for commercial purposes.

We ask you to respect the spirit of open source:

- Keep original author credits and license text intact.
- Do not remove annotations or license statements.
- Do not exploit the rule set for closed-source monetization or abusive purposes.

Additionally, the Aegis project has enabled GPG commit signing to ensure the authenticity and integrity of its codebase. You can verify each commit via GPG signatures to gain higher assurance that the code has not been tampered with.

It is recommended to fork or build upon this repository to save time, maintain compatibility, and benefit from future security updates.

## **🙌  Aegis Telegram Channels**

If you value this project, consider giving it a ⭐️ star and subscribing to updates:

- [Aegis Updates](https://t.me/AegisUpdates) – **Release & Announcements Channel**
- [Aegis Discussion](https://t.me/+xxxxxxxxx) – **Community Group (Invite Only)**

**Group Rules:**

- All members must follow the community guidelines. Offensive, illegal, or spammy behavior will result in permanent ban.
- All uploaded files are scanned by tools such as Dr.Web Bot to prevent malware or trojans.
- No politics, no advertising, no flame wars.
- GitHub account verification is required for contributor access. Help us build a safe, collaborative security community. 