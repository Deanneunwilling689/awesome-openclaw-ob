---
tags:
  - 安全
  - 供应链攻击
  - Skills
  - Snyk
  - ClawHub
aliases:
  - ToxicSkills
  - Snyk ToxicSkills
  - Skills 供应链安全
  - hightower6eu
---

# Snyk ToxicSkills 研究报告

**一句话总结**：Snyk 研究发现 ClawHub 上 36.82% 的 Skills 存在漏洞、341 个已确认恶意，其中单人 hightower6eu 上传了 354 个恶意包，暴露了 AI Agent 生态零审核的供应链灾难。

## 核心数据

| 指标 | 数值 |
|------|------|
| 存在漏洞的 Skills | **36.82%**（1,467 / 3,984） |
| 严重级别问题 | **13.4%**（534 个） |
| 已确认恶意 Skills | **341 个**（感染率 12%） |
| 恶意包上传者 "hightower6eu" | 单人上传 **354** 个恶意包 |
| 发布门槛 | 仅需 1 周以上的 GitHub 账户 |
| 审核机制 | **无代码审查、无签名** |

## 技术分析

### 供应链攻击的根本原因

[[OpenClaw 安全风险|OpenClaw]] 的 Skills 生态系统（ClawHub）采用极低门槛的发布机制：

- **准入条件**：仅需一个注册超过 1 周的 GitHub 账户
- **审核机制**：无人工代码审查、无数字签名验证
- **执行环境**：Skills 在用户的 AI Agent 上下文中运行，天然具有高权限

这与传统包管理器（npm、PyPI）的供应链攻击模式类似，但危害更大——Skills 在受信自动化上下文中执行，可以直接访问 Agent 拥有的所有权限。

### hightower6eu：单人规模化攻击

单个恶意行为者 **hightower6eu** 上传了 **354 个恶意包**，超过了整个平台确认的 341 个恶意 Skills 数量。这表明：

- 批量上传未触发任何自动化检测
- 恶意 Skills 可以在平台上长期存在
- 攻击者可以利用 typosquatting 等策略批量覆盖常用名称

### 漏洞严重度分布

超过三分之一的 Skills 存在安全问题，其中 13.4%（534 个）为**严重级别**，意味着可能导致远程代码执行、[[凭证泄露与信息窃取|凭证泄露]]或数据外泄。

## 与 Atomic Stealer 事件的关联

Snyk 的统计数据在 [[Atomic Stealer 通过 ClawHub 分发]] 事件中得到了验证——ClawHub 下载量第一的 Skill 实际上是恶意软件。1Password 和 Cisco AI Defense 团队独立确认了这一发现。

## 教训与洞察

- ToxicSkills 研究揭示了 [[Skills 市场]] 繁荣表象下的安全债务——36.82% 的漏洞率说明生态增长远远跑在了安全治理前面
- **AI Agent 生态正在重演**开源包管理器的供应链安全问题，但缺乏后者积累的防御能力
- 发布门槛极低 + 零审核 = 攻击者的天堂
- 企业应禁止从 ClawHub 安装未经内部安全审计的 Skills
- 与 [[恶意 Skills 供应链攻击]] 构成完整的供应链威胁分析
- 1Password 在独立研究中验证了 Snyk 的发现

## 相关笔记

- [[恶意 Skills 供应链攻击]]
- [[Atomic Stealer 通过 ClawHub 分发]]
- [[ClawHub 安全整改措施]]
- [[安全边界与风险（总览）]]
- [[代码执行安全]]
- [[暗网讨论分析]]

## 外部链接

- [Snyk Blog - ToxicSkills](https://snyk.io/blog/)
- [Hudson Rock](https://hudsonrock.com)
