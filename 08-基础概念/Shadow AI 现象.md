---
tags:
  - 基础概念
  - 安全
  - 企业治理
  - Shadow-AI
  - 合规
aliases:
  - Shadow AI
  - 影子AI
  - 未授权AI使用
---

# Shadow AI 现象

**一句话总结**：29% 的企业员工在未经 IT 部门批准的情况下使用 AI Agent 工具——就像当年的 Shadow IT，但风险更大，因为 AI Agent 拥有对敏感数据的自主访问和执行能力。

## 核心内容

Shadow AI 是 Shadow IT 的 AI 时代升级版。员工将公司数据喂给未经审批的 AI 工具（包括 [[OpenClaw 是什么|OpenClaw]]），绕过企业安全策略，引入数据泄露、合规违规和供应链攻击风险。

## 详细分析

### 关键数据

员工使用未授权 AI Agent 占 29%——这一数据来自 [[Fortune 500 企业 AI Agent 数据]] 的调研，Fortune 500 中 80%+ 部署活跃 AI Agent，但仅 47% 实施了 GenAI 安全控制，仅 14.4% 有完整审批。

### Shadow AI vs Shadow IT

| 维度 | Shadow IT | Shadow AI |
|------|-----------|-----------|
| 典型行为 | 未授权 SaaS | 使用 ChatGPT、OpenClaw |
| 数据风险 | 存储在未受控平台 | 被 Agent 发送到外部 |
| 执行能力 | 工具不主动操作 | **Agent 自主执行**：发邮件、修改文件 |
| 影响范围 | 局限于数据访问 | 行为不可预测，可能连锁反应 |

### 实际风险场景

1. **BreachForums 事件**：英国公司 CEO 在工作电脑安装 OpenClaw，SSO、凭证、通信历史全暴露，被以 $25,000 出售
2. **Infostealer**：RedLine、Vidar 已将 `~/.openclaw/` 加入窃取列表
3. **大厂禁令**：Meta、Google、Microsoft、Amazon 相继禁止内部使用 OpenClaw

## 关键洞察

Shadow AI 揭示了市场缺口：企业方案（[[Copilot Tasks]]、[[Claude Cowork]]）跟不上需求。[[AI Agent 安全监管趋势|各国监管]]将迫使企业正视这个问题，[[Palo Alto Networks]] 称 OpenClaw 为"2026 年最大的潜在内部威胁"，这也是 [[安全边界与风险（总览）|安全赛道]] 的巨大机会。

## 来源

- [Microsoft Cyber Pulse Report](https://www.microsoft.com/en-us/security/security-insider/emerging-trends/cyber-pulse-ai-security-report)
- [Cato CTRL](https://www.catonetworks.com/blog/cato-ctrl-when-openclaw-ai-personal-assistant-becomes-backdoor/)
- [Dark Reading](https://www.darkreading.com/application-security/coders-adopt-ai-agents-security-pitfalls-lurk-2026)
