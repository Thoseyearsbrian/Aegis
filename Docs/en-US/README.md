**Aegis**



A high-performance, cross-platform rule repository focused on network-layer defense. Designed for Surge, Clash, and OpenWrt. Protects against APT threats, DNS poisoning, malicious C2 traffic, SDK telemetry, and botnet sources. Supports iOS, macOS, Windows, Android, and router platforms.

## *Project Background**

**Aegis** is a personally maintained open-source rule repository dedicated to modern network-layer threat defense. It helps users worldwide build localized, client-side firewall systems by blocking DNS pollution, APT attack infrastructures, SDK tracking domains, backdoor communications, and malicious C2 servers. It includes rules against global high-risk threats such as Pegasus spyware C2 infrastructure and anomalous behavior patterns.

The project enforces encrypted DNS usage and explicitly blocks plaintext DNS requests to ensure communication security, data transparency, and full traffic control. Even on devices like iPhones that lack traditional antivirus software, Aegis provides effective flow-level protection.

## **Key Features**

Aegis is designed to detect and block the following high-risk communications:

- APT command-and-control (C2) infrastructure
- SDK telemetry and behavioral fingerprinting
- DNS poisoning / injection / hijacking behavior
- Botnets, remote access Trojans, and malware C2 channels
- Ad tracking, behavior analytics, and listening CDNs

It supports **Surge**, **Clash**, **QuantumultX**, **OpenWrt**, and other platforms, and works on iOS, macOS, Windows, Android, and router environments. Rules follow a unified structure with professional annotations, making them readable, auditable, and easy to integrate.

## **Philosophy**

Aegis adheres to technical neutrality, information transparency, and complete independence.

I firmly believe every individual has the right to understand and control their network traffic.

Therefore, Aegis does **not** accept any form of commercial investment or capital control. To ensure purity, trust, and security, all configurations are handcrafted and audited by me, with complete annotations to guarantee every rule is transparent, verifiable, and pollution-free.

## *Auto Update**

Aegis uses GitHub-based versioning and automation to stay up to date without manual intervention. It supports remote subscription through Surge, Clash, QuantumultX, and other tools.

## *Download Links**

| **Name**        | **Link**                                                     | **Description**              | **Status** |
| --------------- | ------------------------------------------------------------ | ---------------------------- | ---------- |
| SurgeAegis      | [SurgeAegis](https://raw.githubusercontent.com/Thoseyearsbrian/SurgeAegis) | Surge firewall configuration | Complete   |
| ClashAegis      | [ClashAegis](https://raw.githubusercontent.com/Thoseyearsbrian/ClashAegis) | Clash firewall configuration | Building   |
| QuantumultAegis | [QuantumultAegis](https://raw.githubusercontent.com/Thoseyearsbrian/QuantumultAegis) | QuantumultX firewall rules   | Building   |
| RouterAegis     | [RouterAegis](https://raw.githubusercontent.com/Thoseyearsbrian/RouterAegis) | Router-based configuration   | Building   |

## **Configuration Guide**

Please refer to the [Wiki](https://github.com/Thoseyearsbrian/GeoIP2-CN/wiki/Surge) for detailed setup instructions. Guides are available for:

- Surge (iOS/macOS GUI + config files)
- Quantumult X
- Shadowrocket
- Clash (ClashX, Clash for Android, Clash for Windows, OpenClash)
- Stash (iOS)
- OpenWrt / router platforms

## *⚠️ Notes**

1. **Disable or remove** CN-specific rules such as:

```
RULE-SET,https://raw.githubusercontent.com/Thoseyearsbrian/Aegis/main/SurgeAegis/rules/China.list,DIRECT
GEOIP,CN,DIRECT
```

1. Place GEOIP,CN rule right before the final rule:

```
GEOIP,CN,DIRECT
FINAL,REJECT
```

1. The GeoIP database only includes **mainland China** IPs. Avoid querying other countries:



```
GEOIP,US,PROXY  # ❌ Invalid
GEOIP,HK,PROXY  # ❌ Invalid
GEOIP,CN,DIRECT # ✅ Valid
```

## **🌟 Special Thanks**

This project is inspired by many outstanding community contributions. Key references include:

- **Project Structure**: [@Rabbit-Spec](https://github.com/Rabbit-Spec)
- **Rule Scripts**: [@Nebulosa-Cat](https://github.com/Nebulosa-Cat), [@NobyDa](https://github.com/NobyDa), [@LucaLin233](https://github.com/LucaLin233), [@Hyseen](https://github.com/Hyseen), [@congcong0806](https://github.com/congcong0806), [@fishingworld](https://github.com/fishingworld), [@mieqq](https://github.com/mieqq), [@TributePaulWalker](https://github.com/TributePaulWalker)
- **Routing / Rewrite Rules**: [@blackmatrix7](https://github.com/blackmatrix7)
- **Apple Unlock Rules**: [@VirgilClyne](https://github.com/VirgilClyne)
- **Pegasus IOC**: [@Amnesty International](https://amnesty.org/) for Pegasus C2 blocklist sources

If your work was not properly credited, please contact me. I’ll update the acknowledgements promptly.

## **🔐 Disclaimer**

This is a non-commercial, community-driven open-source rule set for personal security enhancement only.

By using this project, you agree to the following terms:

- Some content is derived from public threat intelligence or open-source projects. All sources are cited. Contact me to remove any disputed content.
- Use at your own risk. Always test before deployment. I am not liable for any disruption or damage caused.
- Commercial use is prohibited without written permission.
- This project is provided “as is” with no warranties. Users assume full responsibility.
- The rules are for lawful use only. Do not use for offensive security, evasion, or malicious purposes.
- Authors disclaim all liability for direct or indirect loss from use of this content.
- I reserve the right to update or remove any part of the repository without notice.

**There are no hidden backdoors, proxy endorsements, or spyware.** All rules are plaintext, self-hosted, open for review, and built for transparency and community trust.

## **🏅 License**

This project is licensed under the [MIT License](https://github.com/EAlyce/conf/blob/main/LICENSE). You are free to use, modify, and distribute this project, even for commercial purposes.

We ask you to respect the spirit of open source:

- Keep original author credits and license text intact.
- Do not remove annotations or license statements.
- Do not exploit the rule set for closed-source monetization or abusive purposes.

It is recommended to fork or build upon this repository to save time, maintain compatibility, and benefit from future security updates.

## **📣 Aegis Telegram Channels**

If you value this project, consider giving it a ⭐️ star and subscribing to updates:

- [Aegis Updates](https://t.me/AegisUpdates) – **Release & Announcements Channel**
- [Aegis Discussion](https://t.me/+xxxxxxxxx) – **Community Group (Invite Only)**

**Group Rules:**

- All members must follow the community guidelines. Offensive, illegal, or spammy behavior will result in permanent ban.
- All uploaded files are scanned by tools such as Dr.Web Bot to prevent malware or trojans.
- No politics, no advertising, no flame wars.
- GitHub account verification is required for contributor access.Help us build a safe, collaborative security community. 