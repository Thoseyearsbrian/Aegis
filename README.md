<h1 align="center">Aegis — Personal Digital Firewall Ruleset for Surge</h1>
<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-en-1.png" width="300"></img>
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-en-2.png" width="300"></img>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License" />
  <img src="https://github.com/Thoseyearsbrian/GeoIP2-CN/actions/workflows/update.yml/badge.svg" alt="GeoIP Auto Update Status" />
  <img src="https://img.shields.io/github/stars/Thoseyearsbrian/Aegis?style=social" alt="GitHub stars" />
  <img src="https://img.shields.io/github/v/release/Thoseyearsbrian/Aegis?include_prereleases&label=version" alt="Version" />
  <img src="https://img.shields.io/github/last-commit/Thoseyearsbrian/Aegis" alt="Last Commit" />
</p>

<p align="center">
  <a href="https://github.com/Thoseyearsbrian/Aegis/blob/main/Docs/zh-CN/README.md"><b>【中文文档点此进入】</b></a>
</p>

A network security ruleset meticulously maintained for Surge, focused on application- and transport-layer defense. It blocks DNS poisoning, APT infrastructure, SDK telemetry, backdoor communications, and C2 controllers. The ruleset also extends to block global advertising, behavioral tracking, and adult content domains — enabling precise, verifiable, and privacy-focused local traffic filtering for iOS and macOS.

## **Overview**

[Aegis](https://github.com/Thoseyearsbrian/Aegis)is a network security rule set developed and maintained long-term by an independent developer. It focuses on countering modern network-layer threats and aims to help global users build localized and effective defense systems. The project blocks DNS poisoning, APT threat sources, SDK telemetry, backdoor domains, and C2 controllers, and further extends its coverage to major global advertising, behavioral tracking, and adult content domains — enabling precise identification and efficient interception of local traffic. It also includes rules for numerous high-risk attack sources worldwide, including communication infrastructure and behavioral signatures related to Pegasus spyware.

The project fully enforces encrypted DNS, rejecting plaintext queries to ensure secure and private communications. Even on devices lacking traditional security software — such as iPhones — Aegis provides effective protection at the network traffic layer.

In addition, Aegis offers an optional advanced module — CA_Block.list — which targets controversial or revoked root certificate authorities, OCSP endpoints, and CRL domains worldwide. This module is designed for users with higher digital trust requirements, helping to reduce the risk of man-in-the-middle attacks and malicious certificate chains.

## **Key Features**

Aegis is designed to detect and block the following high-risk communications:

- Ad tracking, behavior analytics, and listening CDNs
- Botnets, remote access Trojans, and malware C2 channels
- DNS poisoning / injection / hijacking behavior
- APT command-and-control (C2) infrastructure
- SDK telemetry and behavioral fingerprinting

Aegis is specifically designed for the Surge platform, fully compatible with both iOS and macOS systems. It offers excellent readability, auditability, and modular deployment capabilities, making it ideal for various use cases such as policy routing and firewall-assisted configurations.You may optionally enable the advanced module CA_Block.list to block high-risk certificate validation behaviors and CA-related traffic, further enhancing your defense against man-in-the-middle attacks.

## **Philosophy**

Aegis adheres to technical neutrality, information transparency, and complete independence. I firmly believe every individual has the right to understand and control their network traffic. Therefore, Aegis does not accept any form of commercial investment or capital control. To ensure purity, trust, and security, all configurations are handcrafted and audited by me, with complete annotations to guarantee every rule is transparent, verifiable, and pollution-free.

## **Aegis Main Rule Modules**

| Index |          Module Name           | File Name              | Description                                                                                   | Detection Criteria                                                                 |
| :---: | :----------------------------: | ---------------------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| ①     | CA Trust Anomalies             | CA_Block.list          | Blocks untrusted, misused, or revoked Certificate Authorities and related OCSP/CRL endpoints | Involves cases of certificate abuse, rogue issuance, or public revocation records  |
| ②     | Advertisement Tracking         | AdTracking_Block.list  | Covers commercial ad domains, social pixels, analytics SDKs, and third-party tracking scripts | Clear ad-targeted or profiling-related communications, excluding surveillance SDKs |
| ③     | Adult Content Block            | Adult_Block.list       | Includes domains related to major global adult platforms                                              | Explicit pornography and adult content platforms                                  |
| ④     | Interception & Injection Nodes | Inspection_Block.list  | Blocks link-layer or upstream manipulations like DPI, DNS poisoning, HTTP injection, MITM     | Identified manipulation from ISPs or middleboxes altering/redirecting traffic     |
| ⑤     | Behavioral Fingerprinting      | Behavior_Block.list    | Blocks SDKs or cloud services with telemetry/analytics traits based on DNS/TLS/QUIC/CDN cues  | Based on behavioral patterns, protocol fingerprints, excludes ad or passive SDKs  |
| ⑥     | Background Connections         | Background_Block.list  | Blocks silent background callbacks, config uploads, device-to-cloud comms, IoT/NAS SDKs       | Based on frequency, reconnection patterns, and telemetry behavior                 |
| ⑦     | Backdoor & Malicious Infra     | Backdoor_Block.list    | Includes C2 infra of backdoors like RAT, Sliver, Metasploit etc., used for remote access      | Confirmed malicious traffic or infrastructure directly tied to implant attacks    |
| ⑧     | Botnets / Scanners / C2        | Botnet_Block.list      | Aggregates botnet C2s, DDoS nodes, mass scanners, UDP flooders                               | High-frequency, broad distribution, verified as botnet nodes                      |
| ⑨     | APT Threat Actors              | APT_Block.list         | IOC from public APT disclosures with clear org/country labels (APT1 ~ APTxx)                 | Verified by public threat reports and attribution                                  |
| ⑩     | Pegasus Spyware Infrastructure | Pegasus_Block.list     | IOC from Amnesty’s Pegasus reports: C2 nodes, redirects, spyware domains                     | Amnesty-disclosed Pegasus C2s with surveillance risk. Recommended to block                       |

## **Auto Update**

Aegis uses GitHub-based versioning and automation to stay up to date without manual intervention.  It fully supports remote rule subscription for Surge.

## **Configuration Links**

SurgeAegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_CN.conf  
SurgeAegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/config/Spec/SurgeAegis_EN.conf  

## **Configuration Guide**

Copy the configuration link → Open Surge → Download from URL → Paste the link → Edit in Text Mode → Replace your node with the correct parameter → Done!

<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step-en.png" width="600">
</p>

## ⚠️ Notes

1. **Rule Mode must be enabled; otherwise, the Aegis rule set will not function properly**

   ```bash
   Aegis is a personal firewall system specifically designed for Rule Mode. It only works correctly when Surge is set to Rule Mode. 
   If you use Global Mode or Direct Mode, rules will not match, domain/IP classification will fail, and all protection and routing functionalities will be lost.
   ```

2. **Disable or remove CN-specific rules such as:**

   ```bash
   RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/rules/China.list,DIRECT   # Disable or remove similar rules
   GEOIP,CN,DIRECT                                                                                 # Cannot coexist with the rule above
   ```

3. **Place GEOIP,CN rule right before the final rule:**

   ```bash
   # ... other rules ...
   GEOIP,CN,DIRECT   # Recommended to place here
   FINAL,REJECT      # Final rule
   ```

4. **The GeoIP database only includes mainland China IPs. Avoid querying other countries:**

   ```bash
   GEOIP,US,PROXY   # Invalid, no matching records
   GEOIP,AU,PROXY   # Invalid, no matching records
   GEOIP,HK,PROXY   # Invalid, no matching records
   GEOIP,CN,DIRECT  # Valid
   ```

## **🌟 Special Thanks**

This project is built upon inspiration and reference from numerous outstanding open-source initiatives within the GitHub community. We extend our sincere gratitude to all developers who have contributed to the open-source ecosystem.

To meet personal cybersecurity requirements, this project has been deeply customized and optimized for enhanced security based on existing rule sets. In order to ensure the integrity, safety, and long-term availability of the project, all materials and rule files are self-hosted within this repository, thereby avoiding issues such as update failures or trust concerns arising from third-party dependencies.

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

This project is licensed under the [MIT License](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE). You are free to use, modify, and distribute this project, even for commercial purposes.

We ask you to respect the spirit of open source:

- Keep original author credits and license text intact.
- Do not remove annotations or license statements.
- Do not exploit the rule set for closed-source monetization or abusive purposes.

Additionally, the Aegis project has enabled GPG commit signing to ensure the authenticity and integrity of its codebase. You can verify each commit via GPG signatures to gain higher assurance that the code has not been tampered with.

We recommend maintaining and extending your configurations based on the structure of this project, to avoid duplicated efforts, reduce time costs, and benefit from ongoing updates and security optimizations.

## **🙌  Aegis Telegram Channels**

If you value this project, consider giving it a ⭐️ star and subscribing to updates:

- [Aegis Updates](https://t.me/AegisUpdates) – **Release & Announcements Channel** (Coming Soon)
- [Aegis Discussion](https://t.me/+xxxxxxxxx) – **Community Group (Invite Only)** (Coming Soon)

**Group Rules:**

- This group is a pure technical discussion platform. It is strictly forbidden to post content involving politics, pornography, drugs, firearms, explosives, gambling, scams, cryptocurrency speculation, advertising, personal attacks, or any illegal or disruptive behavior (including but not limited to abuse, provocation, spamming, or phishing links). Violators will be dealt with immediately based on the severity of the situation, with serious offenders permanently banned.

- To ensure communication safety, do not upload any unchecked or unverified executable files, archives, scripts, or links of unknown origin. Any confirmed violations will result in immediate banning and blacklisting. All uploaded files and content in the group will be automatically scanned by security tools such as the Dr.Web antivirus bot to prevent the spread of malicious content.

- All members are expected to uphold a professional and respectful environment, focusing on cybersecurity topics and collaborative rule development. Let us work together to build a clean, orderly, and trustworthy community.

- These rules apply to all members without exception. Community supervision and joint maintenance are highly encouraged.