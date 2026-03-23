---
tags:
  - 安全
  - ClawHub
  - OpenClaw
aliases:
  - ClawHavoc 整改
  - Skills 安全审核
---

# ClawHub 安全整改措施

[[ClawHavoc 事件]] 暴露了 [[ClawHub 官方技能注册表|ClawHub]] 的严重安全漏洞（属于供应链攻击的典型案例），随后实施了以下整改：

## 整改措施

### 1. 大规模清理
- 从 5,705 个 Skills 清理至 3,286 个
- 删除 2,419 个可疑 Skills（其中包含凭证窃取类恶意软件）

### 2. VirusTotal 合作
- 2026.2.7 起所有上架 Skills 自动进行恶意软件扫描
- 属于 OpenClaw 安全生态的重要组成部分
- 回应了安全厂商对 OpenClaw 安全问题的批评

### 3. 增强社区审核
- Skills 被举报 3 次后自动隐藏
- 进入人工复审流程
- 是"纵深防御"理念的具体实施

## 整改效果评估

整改措施在一定程度上缓解了 [[致命三合一安全矛盾]] 中"处理不受信任内容"这一环的风险。但暗网论坛显示攻击者已在研究绕过新扫描机制的方法，代码执行安全问题仍需持续关注。

## 相关笔记

- [[ClawHub 官方技能注册表]]
- [[ClawHavoc 事件]]
- [[致命三合一安全矛盾]]
- [[权限控制机制]]
- [[沙箱机制]]

## 外部链接

- [Snyk Blog - Supply Chain Security](https://snyk.io/blog/)
- [NIST AI](https://www.nist.gov/artificial-intelligence)
