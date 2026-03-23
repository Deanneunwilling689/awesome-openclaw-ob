---
tags:
  - CI-CD
  - DevOps
  - 自动化
  - 测试
  - 部署
aliases:
  - CI/CD
  - 持续集成
  - 持续部署
  - CI/CD 流水线
---

# CI/CD 流水线

## 一句话理解

> CI/CD 是"代码提交后自动测试、自动部署"的工程实践——AI Agent 的加入让流水线从"按预设脚本执行"进化到"理解上下文后智能决策"，就像从固定流水线升级为有判断力的质检员。

## 核心概念

### CI/CD 是什么

- **CI（Continuous Integration，持续集成）**：每次代码提交自动触发构建和测试，尽早发现问题
- **CD（Continuous Deployment/Delivery，持续部署/交付）**：测试通过后自动部署到生产环境

传统流水线：`代码提交 → 自动构建 → 运行测试 → 部署生产`——每一步都是预先编写好的脚本，机械执行。

### AI Agent 在 CI/CD 中的角色

AI Agent 正在重塑 CI/CD 的多个环节：

| 环节 | 传统方式 | AI Agent 方式 |
|------|---------|--------------|
| 代码审查 | 人工 PR Review | Agent 自动分析 diff，识别潜在 Bug |
| 测试生成 | 手动编写测试用例 | Agent 根据代码变更自动生成测试 |
| 故障诊断 | 人工查日志 | Agent 语义理解错误日志并建议修复 |
| 部署决策 | 固定规则（全通过则部署） | Agent 评估风险等级后决定是否部署 |

### OpenClaw 生态中的 CI/CD 相关能力

- ClawHub 上 **DevOps & Cloud** 类 Skills 共 212 个，包含 GitHub Actions、Jenkins、ArgoCD 等集成
- **GitHub Skill**（10K 下载）：PR 创建、代码审查、CI 状态监控
- [[Peter Steinberger|Steinberger]] 的激进实践："Prompt Requests" 替代 Pull Requests——不再做传统代码审查，而是让 Agent 理解意图后直接提交

## 应用与影响

- **SWE-Bench 作为基准**：[[SWE-Bench 基准测试|Claude Opus 4.6 在 SWE-Bench 达到 80.8%]]，意味着 AI Agent 在真实代码库修复 Bug 的能力已接近专业开发者，CI/CD 中的自动修复不再是幻想
- **OpenClaw 自身的 CI/CD**：OpenClaw 项目有 15,329+ commits、866+ contributors，其 CI/CD 流水线本身就是 AI 辅助开发的实践案例
- **安全风险**：Veracode 报告显示 **45%** AI 生成代码样本未通过安全测试——CI/CD 流水线中的安全扫描环节变得前所未有地重要

## 关键洞察

CI/CD 流水线正从"自动化"进化为"智能化"。传统 CI/CD 像 Cron——机械按时执行固定脚本；AI 驱动的 CI/CD 更像 [[Heartbeat 主动监控机制|Heartbeat]]——带判断力地检查，理解上下文后决定下一步。但这个转变也意味着流水线本身成为了攻击面，恶意提示注入可能通过 Agent 绕过安全检查直接部署有害代码。

## 双链导航

- [[OpenClaw 是什么]] — CI/CD Skills 依托的框架生态
- [[SWE-Bench 基准测试]] — 衡量 Agent 在 CI/CD 中修复代码能力的标准
- [[Heartbeat 主动监控机制]] — CI/CD 的智能化与 Heartbeat 的理念相通
- [[ClawHub 技能市场]] — DevOps & Cloud 类 Skills 的分发平台
- [[Agentic Coding]] — Agent 在软件开发全生命周期中的角色
