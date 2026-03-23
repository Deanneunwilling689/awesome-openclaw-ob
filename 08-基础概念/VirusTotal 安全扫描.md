---
tags:
  - 安全
  - 恶意软件检测
  - ClawHub
  - 供应链安全
aliases:
  - VirusTotal
  - VT 扫描
  - 恶意软件扫描
---

# VirusTotal 安全扫描

## 一句话理解

> VirusTotal 是 Google 旗下的多引擎恶意软件扫描服务，能同时调用 70+ 杀毒引擎检测文件和 URL 是否有害——ClawHub 在 2026.2.7 后将其集成为 Skills 上架的自动安全门槛。

## 核心概念

### 什么是 VirusTotal

VirusTotal 聚合了全球主流杀毒引擎（CrowdStrike、Kaspersky、Sophos 等 70+），用户上传文件或提交 URL 后，所有引擎同时扫描并出具报告。它不依赖单一引擎的判断，而是用**多引擎交叉验证**降低漏检率。

### 为什么 ClawHub 需要它

[[OpenClaw 是什么|OpenClaw]] 的 [[ClawHub 技能市场]] 在 Snyk ToxicSkills 研究中暴露了严重的供应链风险：

- **36.82%** 的 Skills 存在安全漏洞（1,467/3,984）
- **341 个**已确认恶意 Skills（感染率 12%）
- 单一攻击者 "hightower6eu" 上传了 354 个恶意包
- 发布门槛极低——仅需 1 周以上的 GitHub 账户，无代码审查、无签名

### ClawHub 整合方案（2026.2.7 起）

ClawHavoc 事件后的安全整改措施之一：所有新上架 Skills 自动经过 VirusTotal 扫描，不通过则无法发布。配合社区举报机制（被举报 3 次自动隐藏进入人工复审），从 5,705 个 Skills 清理至 3,286 个，删除 2,419 个可疑 Skills。

## 应用与影响

- **Skill 安全门槛**：从零审核到自动扫描，大幅提高恶意 Skill 的上架成本
- **但非万能**：VirusTotal 擅长检测已知恶意软件特征，但对[[提示注入]]类攻击（恶意指令嵌入自然语言）无能为力
- **生态信任基础**：与 Snyk Agent Trust Hub 共同构成 ClawHub 的安全生态

## 关键洞察

VirusTotal 集成反映了 [[OpenClaw 是什么|OpenClaw]] 生态的根本矛盾：**开放性催生创新，也催生攻击面**。5,705 个社区 Skills 的繁荣与 12% 恶意感染率是同一枚硬币的两面。自动扫描是必要的第一步，但真正的安全需要代码签名、沙箱执行和社区审计的多层防御。

## 外部链接

- [VirusTotal 官方网站](https://virustotal.com)

## 双链导航

- [[OpenClaw 是什么]] — VirusTotal 保护的目标生态
- [[安全边界与风险（总览）]] — Skills 供应链攻击的完整分析
- [[Docker 容器化]] — 运行时沙箱隔离，与上架扫描互补
- [[ClawHub 技能市场]] — VirusTotal 集成的直接受益者
- [[提示注入]] — VirusTotal 无法覆盖的攻击类型
