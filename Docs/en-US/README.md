<!-- Aegis Cover Image -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/Aegis_Cover_Image.png" alt="Aegis Cover Image" width="1200"/>
</p>

<h1 align="center">Aegis — Personal Digital Firewall Ruleset for Surge</h1>
<p align="center">
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-en-1.png" width="300"></img>
<img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-en-2.png" width="300"></img>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License: Apache 2.0" />
  <img src="https://github.com/Thoseyearsbrian/GeoIP2-CN/actions/workflows/update.yml/badge.svg" alt="GeoIP Auto Update Status" />
  <img src="https://img.shields.io/github/stars/Thoseyearsbrian/Aegis?style=social" alt="GitHub stars" />
  <img src="https://img.shields.io/github/v/release/Thoseyearsbrian/Aegis?include_prereleases&label=version" alt="Version" />
  <img src="https://img.shields.io/github/last-commit/Thoseyearsbrian/Aegis" alt="Last Commit" />
</p>

<p align="center">
  <a href="https://github.com/Thoseyearsbrian/Aegis/blob/main/Docs/zh-CN/README.md"><b>【中文文档点此进入】</b></a>
</p>

## **Overview**

[Aegis](https://github.com/Thoseyearsbrian/Aegis) is a meticulously maintained security rule set tailored for Surge, designed to address modern network-layer threats and help users worldwide build localized digital defense systems.The project focuses on blocking DNS poisoning, APT threat sources, SDK telemetry, backdoor domains, C2 controllers, and other potentially malicious communications. It also extends to cover major global advertising networks, behavioral tracking platforms, and adult content domains, enabling precise traffic identification and efficient interception on local devices.  

Aegis includes rule sets targeting high-risk infrastructures used by advanced threat actors worldwide — notably featuring detection strategies and domain blocks related to Pegasus spyware and its associated communication behaviors.

The project fully enforces encrypted DNS, rejecting plaintext queries to ensure secure and private communications. Even on devices lacking traditional security software — such as iPhones — Aegis provides effective protection at the network traffic layer.

## **Key Features**

Aegis is designed to detect and block the following high-risk communications:

- Ad tracking, behavior analytics, and listening CDNs
- Botnets, remote access Trojans, and malware C2 channels
- DNS poisoning / injection / hijacking behavior
- APT command-and-control (C2) infrastructure
- SDK telemetry and behavioral fingerprinting

Aegis is purpose-built for the Surge platform, with full compatibility across both iOS and macOS systems. It features clear readability, audit-friendly structure, and modular deployment, making it suitable for policy-based routing, firewall integration, and other advanced use cases.

An optional advanced module — CA_Block.list — is also available, aimed at blocking globally controversial or publicly revoked root certificate authorities, OCSP responders, and CRL domains. This module is intended for users with heightened digital trust requirements, offering additional protection against man-in-the-middle attacks and malicious certificate chains.

## **Philosophy**

Aegis adheres to technical neutrality, information transparency, and complete independence. I firmly believe every individual has the right to understand and control their network traffic. Therefore, Aegis does not accept any form of commercial investment or capital control. To ensure purity, trust, and security, all configurations are handcrafted and audited by me, with complete annotations to guarantee every rule is transparent, verifiable, and pollution-free.

## **Aegis Main Rule Modules**

| Index |          Module Name           | File Name              | Description                                                                                   | Detection Criteria                                                                 |
| :---: | :----------------------------: | ---------------------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| ①     | Untrusted Certificate Authorities            | CA_Block.list          | Blocks untrusted, misused, or revoked Certificate Authorities and related OCSP/CRL endpoints | Involves cases of certificate abuse, rogue issuance, or public revocation records  |
| ②     | Ad Block       | AdTracking_Block.list  | Covers commercial ad domains, social pixels, analytics SDKs, and third-party tracking scripts | Clear ad-targeted or profiling-related communications, excluding surveillance SDKs |
| ③     | Adult Block           | Adult_Block.list       | Includes domains related to major global adult platforms                                              | Explicit pornography and adult content platforms                                  |
| ④     | Interception of Surveillance Nodes | Inspection_Block.list  | Blocks link-layer or upstream manipulations like DPI, DNS poisoning, HTTP injection, MITM     | Identified manipulation from ISPs or middleboxes altering/redirecting traffic     |
| ⑤     | Behavioral Analysis and Telemetry Node Interception      | Behavior_Block.list    | Blocks SDKs or cloud services with telemetry/analytics traits based on DNS/TLS/QUIC/CDN cues  | Based on behavioral patterns, protocol fingerprints, excludes ad or passive SDKs  |
| ⑥     | Background Callback and Silent Communication Node Blocking         | Background_Block.list  | Blocks silent background callbacks, config uploads, device-to-cloud comms, IoT/NAS SDKs       | Based on frequency, reconnection patterns, and telemetry behavior                 |
| ⑦     | Backdoor Command and Implant Communication Node Blocking     | Backdoor_Block.list    | Includes C2 infra of backdoors like RAT, Sliver, Metasploit etc., used for remote access      | Confirmed malicious traffic or infrastructure directly tied to implant attacks    |
| ⑧     | Botnet Infrastructure and Command Node Blocking        | Botnet_Block.list      | Aggregates botnet C2s, DDoS nodes, mass scanners, UDP flooders                               | High-frequency, broad distribution, verified as botnet nodes                      |
| ⑨     | APT Threat Source Blocking              | APT_Block.list         | IOC from public APT disclosures with clear org/country labels (APT1 ~ APTxx)                 | Verified by public threat reports and attribution                                  |
| ⑩     | Pegasus Spyware Communication Node Blocking | Pegasus_Block.list     | IOC from Amnesty’s Pegasus reports: C2 nodes, redirects, spyware domains                     | Amnesty-disclosed Pegasus C2s with surveillance risk. Recommended to block                       |

## **Auto Update**

Aegis uses GitHub-based versioning and automation to stay up to date without manual intervention.  It fully supports remote rule subscription for Surge.

If configuration auto-reload is not enabled, you can manually refresh external resources or reload the profile to ensure the ruleset stays up to date.

## Surge IPv4 Configuration Links

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_CN.conf  

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_EN.conf

## Surge IPv6 Configuration Links

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_CN.conf  

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_EN.conf

 💡 Note: Please choose the appropriate configuration based on your network environment. If your network natively supports IPv6, use the IPv6 version; otherwise, use the IPv4 version. **Do not mix configurations**, as this may result in request failures or DNS resolution issues.

## **Configuration Guide**

Copy the configuration link → Open Surge → Download from URL → Paste the link → Edit in Text Mode → Replace your node with the correct parameter → Done!

<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step-en.png" width="600">
</p>

## ⚠️ Notes

1. **Rule Mode is mandatory — Aegis cannot perform any filtering, routing, or protection without it**

   ```bash
   Aegis is a personal digital firewall system built entirely on Surge’s Rule Mode. It relies on rule-based matching to classify domains, enforce policies, and block malicious traffic.

   Full functionality is only available when Surge is running in **Rule Mode**. If you switch to Global Mode or Direct Mode, while network access may still work, all rule matching will be bypassed, leading to the following risks:

   • Domains and IPs will not be classified correctly  
   • All filtering mechanisms and strategy modules will be disabled  
   • Core functions like traffic splitting, threat protection, and ad blocking will stop working

   If you encounter a domain temporarily inaccessible due to unmatched rules, you may **switch to Global Mode or Direct Mode temporarily** to regain access. However, we strongly recommend submitting an Issue immediately, so we can update the corresponding rule set and prevent future disruption.
   ```

2. **It is recommended to combine China.list (for domain matching) and GEOIP,CN (for IP segments) for accurate detection of Chinese traffic:**

   ```bash
   RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/rules/China.list, DIRECT   # Precisely matches Chinese domains
   GEOIP,CN,DIRECT                                                                                  # Matches traffic from Chinese IPs not in domain list
   FINAL,REJECT                                                                                     # Final fallback rule (do NOT place GEOIP below this)
   ```

3. **Do NOT use GEOIP rules for countries outside mainland China — the current database only supports CN records**

   ```bash
   GEOIP, US, PROXY   # Invalid — No matching records available
   GEOIP, AU, PROXY   # Invalid — No matching records available
   GEOIP, CN, DIRECT  # Valid — Supported and recognized
   ```

4. **Explanation for the message “tun-excluded-routes parameter configured, may cause issues after switching networks”**

   ```bash
   This message is not an error or conflict but a system-level reminder from Surge.  
   It can be safely ignored in a fixed network environment.  
   If you experience temporary LAN communication issues (e.g., AirDrop, Bonjour, or NAS) after switching networks such as Wi-Fi ↔ hotspot, select “Stop Proxy” → “Start Proxy” in the menu to rebuild the routing table and restore connectivity.
   ```

## **🌟 Special Thanks**

This project is built upon inspiration and reference from numerous outstanding open-source initiatives within the GitHub community. We extend our sincere gratitude to all developers who have contributed to the open-source ecosystem.

To meet personal cybersecurity requirements, this project has been deeply customized and optimized for enhanced security based on existing rule sets. In order to ensure the integrity, safety, and long-term availability of the project, all materials and rule files are self-hosted within this repository, thereby avoiding issues such as update failures or trust concerns arising from third-party dependencies.

**Project Structure**: 

[@Rabbit-Spec](https://github.com/Rabbit-Spec) 👉 The primary reference for the overall project architecture and rule logic. The current version has undergone extensive restructuring and security adaptation based on this foundation.

[@AmnestyTech](https://github.com/AmnestyTech)  👉 Provided Pegasus-related IOC data as a critical source for rule construction.

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

**Author’s Statement**: This project does not engage in malicious activities, does not include hidden backdoors or monitoring mechanisms, does not promote proxy services, and contains no obfuscated or harmful logic. All rule contents are written in plain text, fully commented, structured clearly, and hosted solely within this repository for community review, audit, and traceability.

## **🏅 License**

This project is licensed under the [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE). You are free to use, modify, and distribute this project, even for commercial purposes.

We ask you to respect the spirit of open source:

- Keep original author credits and license text intact.
- Do not remove annotations or license statements.
- Do not exploit the rule set for closed-source monetization or abusive purposes.

Additionally, the Aegis project has enabled GPG commit signing to ensure the authenticity and integrity of its codebase. You can verify each commit via GPG signatures to gain higher assurance that the code has not been tampered with.

## 🙌 Community Support

If you find this project valuable, feel free to Star ⭐️ it. All rule updates are announced through our Telegram channels — you're welcome to subscribe and stay informed:

**Telegram Release Channel** - <a href="https://t.me/aegisupdates" target="_blank">Aegis Updates</a> : Publishes the latest rule versions, changelogs, and important announcements  

**Telegram Community Group** - <a href="https://t.me/aegisdiscussion" target="_blank">Aegis Discussion</a> : Share suggestions, report false positives, and participate in collaborative rule development