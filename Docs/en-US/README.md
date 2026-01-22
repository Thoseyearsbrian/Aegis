<!-- Aegis Logo -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/assets/Aegis_Cover_Image.png" alt="Aegis Cover Image"/>
</p>

<h1 align="center">Aegis — Personal Digital Firewall Ruleset for Surge</h1>
<p align="center">
  <img
    src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-en-1.png"
    width="300"
    alt="Surge iOS: Aegis_EN configuration overview interface screenshot"
  />
  <img
    src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/group-policy-mobile-en-2.png"
    width="300"
    alt="Surge iOS: Aegis_EN policy group interface screenshot"
  />
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
    href="https://github.com/Thoseyearsbrian/Aegis/blob/main/Docs/zh-TC/README.md"
    title="查看 Aegis 繁體中文文檔"
    aria-label="Aegis 專案的繁體中文文檔"
  >
    <b>【繁體中文文檔點此進入】</b>
  </a>
</p>

## **Overview**

Personal digital firewall ruleset for [Surge](https://nssurge.com), focused on identifying potential communication threats at both the application-layer and transport-layer. It covers a broad range of suspicious behaviors including [DNS poisoning](https://en.wikipedia.org/wiki/DNS_hijacking), [APT threat sources](https://en.wikipedia.org/wiki/Advanced_persistent_threat), [SDK telemetry](https://en.wikipedia.org/wiki/Software_development_kit), [Backdoor communication](https://en.wikipedia.org/wiki/Back_door), [PCDN relay communication](https://en.wikipedia.org/wiki/P2P_caching), [C2 controllers](https://en.wikipedia.org/?redirect=no&title=Command_and_control), and other potentially malicious communications. The project also expands domain-based identification to major global advertising platforms, behavioral tracking services, and adult content sites, Help users achieve precise local traffic identification and classification on iOS and macOS, and define routing strategies based on their own needs.

In addition, the project incorporates rule sets targeting globally recognized high-risk threat infrastructures, including detection strategies for [Pegasus](https://en.wikipedia.org/wiki/Pegasus_(spyware))￼ spyware and its associated command-and-control infrastructure.

The project fully enforces encrypted DNS, rejecting plaintext queries to ensure secure and private communications. Even on devices lacking traditional security software — such as iPhones — Aegis provides effective protection at the network traffic layer.

## **Key Features**

The Aegis rule set is dedicated to identifying and classifying the following high-risk communication behaviors:

- Ad domain identification, behavioral tracking, and surveillance-style CDN nodes
- PCDN relay traffic and shared-bandwidth transmission
- Botnets, remote access Trojans, and malware C2 channels
- SDK telemetry and behavioral fingerprinting
- APT command-and-control (C2) infrastructure
- DNS poisoning / injection / hijacking behavior

Aegis is purpose-built for the Surge platform, fully compatible with both iOS and macOS. It offers high readability, auditability, and modular deployment — making it suitable for policy-based routing, communication analysis, and enhanced security configurations.

An optional advanced module — CA_Block.list — is also available, aimed at blocking globally controversial or publicly revoked root certificate authorities, OCSP responders, and CRL domains. This module is intended for users with heightened digital trust requirements, offering additional protection against man-in-the-middle attacks and malicious certificate chains.

## **Philosophy**

Aegis adheres to technical neutrality, information transparency, and independent autonomy. I firmly believe every individual has the right to understand and control their network traffic. Therefore, Aegis does not accept any form of commercial investment or capital control. To ensure purity, trust, and security, all configurations are handcrafted and audited by me, with complete annotations to guarantee every rule is transparent, verifiable, and pollution-free.

## **Aegis Main Rule Modules**

| Module ID | Module Name | File Name | Description | Criteria |
| :-------: | :---------: | :------------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ① | Untrusted Certificate Authorities | CA_Block.list | Flags CA root certificates, OCSP endpoints, and CRL domains with known incidents of misuse or revocation. Recommended for scenarios requiring enhanced digital trust. (Advanced Module – Disabled by Default) | Involves cases of certificate misuse, unauthorized issuance, or public revocation records |
| ② | Advertising Domain Detection | AdDomain.list | Covers domains used in commercial advertising delivery, social pixel tracking, behavioral analytics, and third-party SDK statistics (Identification Module - Disabled by Default) | Identified based on behavioral patterns and data collection models, distinguished from telemetry-related communications |
| ③ | Adult Content Domain Detection | AdultDomain.list | Covers domains related to major global adult content platforms (Identification Module - Disabled by default) | Domains directly associated with adult content distribution |
| ④ | PCDN Communication Detection | PCDNDomain.list | Identifies link behaviors suspected to use “shared bandwidth” models, involving device relays, cache nodes, and distributed delivery networks (Identification Module - Disabled by Default) | Identified based on traffic patterns and node distribution consistent with multi-hop relay and cache characteristics |
| ⑤ | Traffic Inspection & Node Detection | InspectionDomain.list | Detects active network-level interventions such as DPI probing, DNS poisoning, HTTP injection, and MITM eavesdropping (Identification Module - Disabled by Default) | Identified based on traffic anomalies like tampering, redirection, and injection, commonly seen in manipulated network environments |
| ⑥ | Behavioral Analytics / Telemetry Node Detection | BehaviorDomain.list | Flags cloud service nodes with identifiable behavioral fingerprinting, including telemetry SDKs, analytics platforms, and behavioral modeling services (Identification Module - Disabled by Default) | Focused on behavior-analytic SDK communication patterns via DNS/TLS traffic; excludes ad or data-upload SDKs |
| ⑦ | Background Reconnections & Silent Communication Blocking | Background_Block.list | Identifies domains used by IoT, NAS, or SDKs for config uploads or device callbacks, aiding detection of stealth telemetry communications (Blocking Module – Enabled by Default) | Focused on background connection behavior via callback frequency, paths, and data uploads; excludes ad and analytics SDKs |
| ⑧ | Backdoor Control & Implant Communication Blocking | Backdoor_Block.list | Blocks known malicious infrastructure involving remote access tools (RATs), reverse shells, heartbeat signals, etc. (Blocking Module – Enabled by Default) | Clearly associated with malicious traffic or exploit backdoors |
| ⑨ | Botnet & Command Node Blocking | Botnet_Block.list | Blocks known botnet controllers, DDoS nodes, and mass-control infrastructure (Blocking Module – Enabled by Default) | Based on public threat intelligence with confirmed attribution and verifiable IoCs |
| ⑩ | APT Threat Source Blocking | APT_Block.list | Blocks C2 infrastructure used by known APT groups, with national attribution tags and intelligence source references (Blocking Module – Enabled by Default) | Derived from public threat intelligence with reliable attribution and IoC chains |
| ⑪ | Pegasus Spyware Communication Blocking | Pegasus_Block.list | Contains domains disclosed by Amnesty used by Pegasus spyware for C2 communication (Blocking Module – Enabled by Default) | Based on Amnesty’s public disclosures of Pegasus C2 infrastructure, indicating high surveillance risk |
| ⑫ | Phishing Domain Blocking | Phishing_Block.list | Blocks domains associated with phishing attacks, including spoofed login pages, fake official sites, and links in deceptive emails. Typical targets of social engineering campaigns. (Blocking Module – Enabled by Default) | Based on public threat intelligence with confirmed attribution and verifiable IoCs |
| ⑬ | Scam Domain Blocking | Scam_Block.list | Blocks suspicious domains with extremely low reputation, reported fraud, fake services, or user complaints. (Blocking Module – Enabled by Default) | Based on public threat intelligence with confirmed attribution and verifiable IoCs | 
| ⑭ | Risk Communication Observation List | Quarantine_Block.list | Covers domains and IPs that are not yet confirmed as malicious but exhibit anomalous communication behaviors, including opaque purposes or the use of non-public protocols or non-standard ports. A quarantine-based blocking strategy is applied by default to mitigate potential risks.(Observation Module – Enabled by Default) | Identified through anomalous communication behavior analysis; the risk has not been conclusively classified as malicious and is placed under isolation and observation for further review |

## **Auto Update**

Aegis is hosted on [GitHub](https://github.com) with an automated update mechanism, ensuring that all rule sets remain up-to-date and are fully compatible with remote subscription in Surge.

If configuration auto-reload is not enabled, you can manually refresh external resources or reload the profile to ensure the ruleset stays up to date.

### Versioning

Aegis follows the [Semantic Versioning](https://semver.org/) : vMAJOR.MINOR.PATCH  e.g., Aegis v3.0.1,MAJOR=3、MINOR=0、PATCH=1

MAJOR (X) : Major changes in structure or compatibility  👉 Requires re-downloading the configuration and re-adding nodes

MINOR (Y) : New policy groups, new modules, or new features  👉 Recommended to re-download the configuration and re-add nodes

PATCH (Z) : Rule fixes, annotation updates, minor improvements  👉 No need to re-download the configuration; updating external resources is sufficient

💡 It is recommended to enable 「Automatically reload if the profile was modified externally/remotely」.This option only applies to automatic reloading when the configuration file (.conf) changes.PATCH updates still require manually refreshing external resources (RULE-SET) to take effect.

Examples:

-	Current version: Aegis v2.0.0,Previous version: Aegis v1.2.4,This is a MAJOR update (MAJOR = 2).You must re-download the configuration and re-add nodes.External resources will be updated automatically.

-	Current version: Aegis v3.3.0,Previous version: Aegis v3.2.2,This is a MINOR update (MINOR = 3).It is recommended to re-download the configuration and re-add nodes.External resources will be updated automatically.

-	Current version: Aegis v3.3.4,Previous version: Aegis v3.3.3,This is a PATCH update (PATCH = 4).No need to re-download the configuration.You only need to manually refresh external resources (RULE-SET).

Summary:

As long as you re-download the configuration file (.conf) and re-add the nodes, external resources will be updated automatically if the option 「Automatically reload if the profile was modified externally/remotely」 is enabled.

For PATCH version updates, you still need to manually refresh external resources (RULE-SET) for the changes to take effect.

## Surge IPv4 Configuration Links

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_CN.conf

Aegis (TC): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_TC.conf

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_EN.conf

## Surge IPv6 Configuration Links

Aegis (CN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_CN.conf

Aegis (TC): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_TC.conf 

Aegis (EN): https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Surge/config/Spec/Aegis_IPv6_EN.conf

 💡 Note: Please choose the appropriate configuration based on your network environment. If your network natively supports IPv6, use the IPv6 version; otherwise, use the IPv4 version. **Do not mix configurations**, as this may result in request failures or DNS resolution issues.

## **Configuration Guide**

Copy the configuration link → Open Surge → Download from URL → Paste the link → Edit in Text Mode → Replace your node with the correct parameter → Done!

<p align="center">
  <img
    src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/surge-config-import-guide-step-by-step-en.png"
    width="600"
    alt="Surge iOS: Aegis_EN ruleset import step-by-step diagram (English)"
  >
</p>

### Video Tutorial

Please select the platform you are using and visit the corresponding video tutorial page:

Beginner-Friendly Surge Guide · iOS (4K) ｜ Click the cover image to watch on YouTube

<p align="center">
<a href="https://youtu.be/cKhRdQF5FTo">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/beginner-friendly-surge-guide-ios-4k.png"
       alt="Beginner-Friendly Surge Guide · iOS (4K)"
       width="600" />
</a>
</p>

Beginner-Friendly Surge Guide · macOS (4K) ｜ Click the cover image to watch on YouTube

<p align="center">
<a href="https://youtu.be/ano6ysBlD5s">
  <img src="https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/Icons/Groups/beginner-friendly-surge-guide-macos-4k.png"
       alt="Beginner-Friendly Surge Guide · macOS (4K)"
       width="600" />
</a>
</p>

## ⚠️ Important Notes

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

3. **Supports GEOIP query rules for countries outside mainland China, as the current database supports global country IP ranges.**

   ```bash
   GEOIP,US, PROXY   # Valid
   GEOIP,AU, PROXY   # Valid
   GEOIP,CN, DIRECT  # Valid
   ```

4. **Explanation for the message “tun-excluded-routes parameter configured, may cause issues after switching networks”**

   ```bash
   This message is not an error or conflict but a system-level reminder from Surge.  
   It can be safely ignored in a fixed network environment.  
   If you experience temporary LAN communication issues (e.g., AirDrop, Bonjour, or NAS) after switching networks such as Wi-Fi ↔ hotspot, select “Stop Proxy” → “Start Proxy” in the menu to rebuild the routing table and restore connectivity.
   ```

## **🌟 Special Thanks**

This project is built upon inspiration and reference from numerous outstanding open-source initiatives within the [GitHub](https://github.com) community. We extend our sincere gratitude to all developers who have contributed to the open-source ecosystem.

To meet personal cybersecurity requirements, this project has been deeply customized and optimized for enhanced security based on existing rule sets. In order to ensure the integrity, safety, and long-term availability of the project, all materials and rule files are self-hosted within this repository, thereby avoiding issues such as update failures or trust concerns arising from third-party dependencies.

### ✍️ Foundational References

[@Rabbit-Spec](https://github.com/Rabbit-Spec) 👉 The primary reference for the overall project architecture and rule logic. The current version has undergone extensive restructuring and security adaptation based on this foundation.

[@AmnestyTech](https://github.com/AmnestyTech) 👉 Provided [Pegasus](https://raw.githubusercontent.com/AmnestyTech/investigations/master/2021-07-18_nso/domains.txt)–related IOC data, serving as a key intelligence source for rule construction ([CC BY 2.0 License](https://creativecommons.org/licenses/by/2.0/)).

[@ESET](https://github.com/eset) 👉 Provides data from the public [malware-ioc](https://github.com/eset/malware-ioc) repository, serving as an important source of intelligence for APT-related rule development ([BSD 2‑Clause License](https://github.com/eset/malware-ioc/blob/master/LICENSE)).

### 🎖️ Major Contributors

[@mieqq](https://github.com/mieqq)￼ 👉 A key contributor to the Chinese Surge community. The [mieqq repository](https://github.com/mieqq/mieqq)￼ has consistently maintained a variety of rules and modules, playing a significant role in the early development and promotion of the ecosystem.

The above acknowledgements are listed in no particular order.If you believe your work is missing from the acknowledgements, please feel free to contact me — I will add it promptly.

## **🔐 Disclaimer**

This project is a non-profit, open-source security rule set aimed at helping users enhance their network defense capabilities. By using this project, you acknowledge that you have read, understood, and agreed to the following terms:

This project is a non-commercial, open-source security rule set intended to help users enhance their network security posture. By using this project, you acknowledge that you have read, understood, and agreed to the following terms:

1. **Third-Party Source Notice**: Portions of this project reference publicly available threat intelligence (e.g., security community reports, threat databases, GitHub projects). All such references are properly cited. If you believe there is an issue, please contact us for correction or removal.
2. **Module Activation Statement**: This project adheres to the principles of technical neutrality, information transparency, and independent autonomy. The rule set is designed to assist users in identifying potentially risky communication behaviors. All identification modules are disabled by default. The formulation and activation of related strategies are entirely at the user’s own discretion. The project author assumes no responsibility for any communication risks resulting from user configurations.
3. **False Positive Warning**: As the rule sets may include generalized blocking strategies, users are advised to conduct thorough testing before deployment to ensure normal business operations are not affected. The project author bears no responsibility for connection disruptions, functional issues, or other consequences caused by false positives.
4. **Commercial Use Notice**: This project is released under the [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE). You are free to use it for both commercial and non-commercial purposes, provided you comply with the license terms, including attribution and documentation requirements. We strongly oppose abuse of the rule set for closed-source development, infringement of public interest, or any actions contrary to the spirit of open-source.
5. **No Warranty Clause**: This project is provided “as is” without any express or implied warranties regarding its completeness, accuracy, timeliness, or suitability. Users must assess applicability on their own and bear all associated risks.
6. **Usage Restrictions**: All rules and configuration files are intended solely for lawful purposes such as network defense, traffic identification, and security research. Any use for offensive actions, reverse engineering, audit bypassing, or illegal activities is strictly prohibited.
7. **Limitation of Liability**: The project author shall not be held liable for any direct or indirect damages (including but not limited to data breaches, business disruption, or security failures) resulting from the use, replication, or distribution of this project.
8. **Right to Modify**: The project author reserves the right to update, modify, or remove any content or disclaimer clauses at any time without prior notice. It is recommended that users periodically review the repository for the latest version.

**Author’s Statement**: This project does not engage in malicious activities, does not include hidden backdoors or monitoring mechanisms, does not promote proxy services, and contains no obfuscated or harmful logic. All rule contents are written in plain text, fully commented, structured clearly, and hosted solely within this repository for community review, audit, and traceability.

## **🏅 License**

This project is licensed under the [Apache License 2.0](https://github.com/Thoseyearsbrian/Aegis/blob/main/LICENSE). You are free to use, modify, and distribute this project, even for commercial purposes.

We ask you to respect the spirit of open source:

- **Keep original author credits and license text intact.**
- **Do not remove annotations or license statements.**
- **Do not exploit the rule set for closed-source monetization or abusive purposes.**

Additionally, the Aegis project has enabled [GPG](https://gnupg.org) commit signing to ensure the authenticity and integrity of its codebase. You can verify each commit via GPG signatures to gain higher assurance that the code has not been tampered with.

## 🙌 Community Support

If you find value in this project, please consider giving it a ⭐️ Star. Relevant Chinese update notes will be published simultaneously via the [Telegram](https://telegram.org) notification channel — feel free to subscribe and stay informed.

**Telegram Update Channel** – <a href="https://t.me/aegisupdates" target="_blank">Aegis Updates</a>: Publishes the latest rule versions, changelogs, and important announcements.