---
name: Rule Contribution
about: Submit new rule entries or suggest modifications to existing ones to enhance
  detection accuracy and modular completeness.
title: "[RULE] <规则贡献 - 请简述标题>"
labels: ['ruleset']
assignees: ''

---

📝 Rule Contribution  -  规则提交

Thank you for your contribution! Please complete the form below to propose new rules. We will review and decide whether to include them.  -  感谢你的贡献！请根据以下格式提交规则，我们将在审核后决定是否采纳。

---

🗂️ Affected Module  -  相关模块

Please select the module(s) this suggestion relates to.  -  请选择你希望新增或改进的模块（可多选）

Tip: Type a lowercase `x` inside `[ ]` to check the box, like `[x]`.  -  提示：在 `[ ]` 内输入小写 `x` 即可勾选，例如 `[x]`

- [ ] AdTracking_Block.list  
- [ ] Adult_Block.list  
- [ ] Apple.list  
- [ ] APT_Block.list  
- [ ] Backdoor_Block.list  
- [ ] Background_Block.list  
- [ ] Behavior_Block.list  
- [ ] Botnet_Block.list  
- [ ] CA_Block.list  
- [ ] China.list  
- [ ] ChinaMedia.list  
- [ ] Crypto.list  
- [ ] GamePlatforms.list  
- [ ] GitHub.list  
- [ ] GlobalMedia.list  
- [ ] Google.list  
- [ ] Inspection_Block.list  
- [ ] Microsoft.list  
- [ ] OpenAI.list  
- [ ] PCDN_Block.list  
- [ ] Pegasus_Block.list  
- [ ] Proxy.list  
- [ ] Telegram.list  
- [ ] WeChat.list  
- [ ] Others (please specify): `_____________`  

---

📱 Platform  -  使用平台 （可选）
 
Select the platform(s) where the issue occurred:  -  请选择你使用的平台环境（可多选） 

- [ ] Surge (iOS)  
- [ ] Surge (macOS)  

---

🙌 Contribution Description - 贡献说明

Please paste one or more complete rule entries, including your suggested annotation if applicable.  -  请直接粘贴完整的规则条目，如包含注释建议，请一并填写（支持多行）。

e.g.: - 例如:

DOMAIN-SUFFIX,example.com  # SDK tracking domain used for behavioral data collection  -  SDK监听域名，用于行为采集

IP-CIDR,192.0.2.0  # Botnet callback IP, source: security vendor report  -  僵尸网络回传IP，来源：某安全厂商报告

> Describe here...  -  在此填写描述...

`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`
`__________________________________________________________________________________________________________________________________`

---

📎 Additional Context (Optional)  -  附加信息（可选）

If you have any relevant references, screenshots, mockups, or sources of inspiration, please include them here.  -  如果你有参考资料、截图或灵感来源，请一并附上。

👉 Paste, drop, or click to add files below.  -  可直接粘贴、拖拽文件，或点击下方“Attach files”图标上传。

---

🤝 Thank you for your contribution! We will carefully review each submitted rule and consider merging it in future releases.  -  感谢你的支持！我们会认真审核每一条贡献规则，并在后续版本中考虑合并。
