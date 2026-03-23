---
tags:
  - OpenClaw
  - 产品定义
  - AI-Agent
aliases:
  - OpenClaw
  - OpenClaw 定义
  - OpenClaw 概览
---

# OpenClaw 是什么

OpenClaw 是一个**免费、开源的自主 AI Agent 框架**，运行在用户本地设备上，通过 WhatsApp、Telegram、Discord 等即时通讯应用作为交互界面，连接外部大语言模型（Claude、GPT、DeepSeek 等）来自主执行任务。

> "Your own personal AI assistant. Any OS. Any Platform. The lobster way."

## 产品定位

OpenClaw 将 AI Agent 视为**基础设施问题**而非仅仅是提示工程问题。LLM 负责智能，OpenClaw 负责操作系统层——会话管理、记忆系统、工具沙箱、访问控制和消息路由。

> "OpenClaw treats AI as an infrastructure problem. The LLM provides intelligence; OpenClaw provides the operating system."

## 核心能力

1. **多频道收件箱**：支持 13+ 通讯平台（WhatsApp、Telegram、Slack、Discord、Signal、iMessage、Teams 等）
2. **多代理路由**：不同频道/对话路由到隔离的 Agent 实例
3. **语音唤醒 + 对话模式**：macOS/iOS/Android 常驻语音，集成 ElevenLabs
4. **Live Canvas**：Agent 驱动的可视化工作空间（A2UI: Agent-to-UI）
5. **浏览器控制**：通过 Chrome DevTools Protocol 控制浏览器
6. **技能/插件系统**：ClawHub 上 5,705 个社区技能
7. **持久记忆**：SQLite + 向量嵌入的混合搜索记忆系统
8. **Heartbeat 主动监控**：每 30 分钟检查一次，主动通知用户

## 关键数据（截至 2026.2.28）

| 指标 | 数值 |
|------|------|
| GitHub Stars | ~237,000（GitHub 全站排名第 15，软件项目排名第 5） |
| Contributors | 866+ |
| 开源许可 | MIT License |
| 主要语言 | TypeScript |
| npm 包名 | `openclaw` |
| 创建时间 | 2025年11月24日 |
| Discord 成员 | 116,000+ |

## 为什么重要

OpenClaw **没有发明新的 AI 技术**。它的创新在于**工程整合**：
1. 把 LLM 的能力包装成"操作系统"
2. 用聊天应用作为通用 UI（人人都会用 WhatsApp）
3. 持久记忆让 Agent 成为真正的"助理"而非"一次性工具"
4. 开源 + 模型无关 = 任何人都能定制

> 不是技术突破，而是**[[可及性突破]]**。

## 最新动态（2026年3月）

- **GitHub Stars 超 28 万**：截至 2026 年 3 月中旬，OpenClaw 的 GitHub 星标数已突破 **280,000**，较 2 月底的 237,000 增长约 18%，继续保持 GitHub 全站 Top 15 的位置
- **[[OpenClaw v2026.3 版本更新|v2026.3 系列版本]]**：3 月是架构大变革月——[[Dashboard 控制面板]] 全面模块化、Ollama/vLLM/SGLang 迁移到 [[Provider-Plugin 架构]]、[[可插拔沙箱后端]] 引入 OpenShell、插件 SDK 路径 Breaking Change
- 在 [[Anthropic Agentic Coding 趋势报告]] 中，OpenClaw 被多次引用为"Agent 民主化"的标杆项目
- 安全方面仍需关注：AI Agent 安全态势中的 1184 个恶意 Skills 数据对 ClawHub 生态构成持续压力

## 相关笔记

- [[OpenClaw 的起源与发展历程]]
- [[OpenClaw v2026.3 版本更新]] — 2026 年 3 月架构大变革
- [[Dashboard 控制面板]] — Web 管理界面
- [[Provider-Plugin 架构]] — 模型提供商插件化
- [[可插拔沙箱后端]] — 可替换的执行环境
- [[Agent Execution Loop]]
- [[Agent-Flow-Loop 原理]]
- [[Tool Use 机制]]
- [[安全边界与风险（总览）]]
- [[Claude Code 的技术架构]]

## 参考

- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
- [Anthropic 官网](https://anthropic.com)
