---
name: Rule Contribution
about: Describe this issue template's purpose here.
title: "[Rule] 规则贡献 - 请填写标题"
labels: ''
assignees: ''

---

📝 Rule Contribution | 规则提交

Thank you for your contribution! Please complete the form below to propose new rules. We will review and decide whether to include them.

感谢你的贡献！请根据以下格式提交规则，我们将在审核后决定是否采纳。

🙌 Contribution Description | 贡献说明

Briefly describe the purpose, background, or threat context of this rule.

请简要描述你添加该规则的目的、背景或威胁来源。

📋 Suggested Rule Line(s) | 建议规则条目

Please paste the rule line(s) you suggest to add (multiple lines supported).

请直接粘贴你建议添加的规则条目（支持多行）。

🗂️ Suggested Target Module | 推荐模块归属
	•	Proxy.list
	•	APT.list
	•	CA_Block.list
	•	AdTracking_Block.list
	•	Background_Block.list
	•	Behavior_Fingerprint.list
	•	Others (please specify) / 其他（请注明）: _____________

⸻

💡 Suggested Annotation (Optional)| 注释建议（可选）

You can provide a recommended annotation/comment for the rule (if applicable).

请提供你建议用于该条目的注释内容（若适用）。

e.g.: / 例如

DOMAIN-SUFFIX,example.com  # SDK tracking domain used for behavioral data collection 
DOMAIN-SUFFIX,example.com  # SDK监听域名，用于行为采集

IP-CIDR,192.0.2.0  # Botnet callback IP, source: security vendor report 
IP-CIDR,192.0.2.0  # 僵尸网络回传IP，来源：某安全厂商报告

📱Platform (Optional) | 使用平台（可选）
	•	Surge (iOS)
	•	Surge (macOS)
	•	Quantumult X
	•	Clash / Clash.Meta
	•	Others / 其他 : ___________

🤝 Thank you for your support! We will evaluate and consider merging your contribution in future releases.

🤝 感谢你的支持！我们将在后续版本中评估并考虑合并你的贡献。
