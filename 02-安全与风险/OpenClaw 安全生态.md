---
tags:
  - 安全
  - 生态系统
  - OpenClaw
aliases:
  - 安全工具生态
  - Security Ecosystem
---

# OpenClaw 安全生态

鉴于 [[ClawHavoc 事件]] 暴露的安全问题，围绕 OpenClaw 已形成专门的安全工具生态。

## 安全工具列表

| 工具 | 提供者 | 功能 |
|------|--------|------|
| Skill Security Scanner | Snyk | 扫描恶意技能 |
| Agent Trust Hub | Snyk | 技能信任评级 |
| 安全加固指南 | Docker | Docker 沙箱最佳实践 |
| 安全加固指南 | Hostinger | 全面安全配置教程 |
| 安全加固指南 | Contabo | 2026 安全指南 |
| 安全部署 | Daytona | 安全沙箱运行 |

## 安全层次

1. **Skills 层面**：[[ClawHub 安全整改措施]] — VirusTotal 扫描 + 社区举报机制
2. **运行时层面**：Docker 沙箱、Daytona 安全沙箱
3. **评估层面**：Snyk 的信任评级系统

这些安全措施是对 [[致命三合一安全矛盾]] 的实际应对。[[OpenClaw 官方安全模型]] 与第三方安全生态共同构成了多层防御体系。

## 相关笔记

- [[ClawHub 安全整改措施]]
- [[ClawHavoc 事件]]
- [[OpenClaw 官方安全模型]]
- [[2026年3月安全公告汇总]] — 最新 GHSA 安全公告

> 来源：[Snyk - ToxicSkills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | [Docker - Run Securely](https://www.docker.com/blog/run-openclaw-securely-in-docker-sandboxes/)
