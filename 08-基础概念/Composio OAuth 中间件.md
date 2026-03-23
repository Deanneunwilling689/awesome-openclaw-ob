---
title: Composio OAuth 中间件
aliases: [Composio, OAuth 中间件, API 授权简化]
tags: [Composio, OAuth, API, SetupClaw, 非技术用户, OpenClaw]
created: 2026-03-15
updated: 2026-03-15
---

## 一句话总结

Composio 是一个 OAuth 中间件服务，为非技术用户解决了 API 授权的"最后一公里"问题——它是 SetupClaw 白手套部署服务的核心技术。

## 核心功能

OAuth 授权对开发者来说是日常操作，但对普通用户来说几乎是不可逾越的障碍：注册开发者账号、创建应用、获取 Client ID/Secret、处理回调 URL、管理 Token 刷新……Composio 将这一切封装为"点击授权"的体验。

关键能力：
- **统一授权入口**：一个界面连接 Gmail、Google Calendar、Notion、Todoist 等数十种服务
- **Token 自动管理**：刷新、续期、失效检测全部自动化
- **预构建集成**：常用 SaaS 服务的 OAuth 流程已经预先配置好
- **面向 AI Agent**：专为 Agent 工具调用场景设计的授权层

## OpenClaw 中的应用

OpenClaw 的 [[可及性突破|可及性]] 瓶颈之一就是 API 授权配置。即使聊天界面人人会用，连接 Gmail 或 Google Calendar 仍需要创建 OAuth 凭证——这就是 [[白手套部署服务|白手套服务]] 存在的原因。

**SetupClaw 的 Composio 实践**：
- 面向 **4-50 人团队**的 CEO/CFO，完全不懂技术
- 使用 Composio 作为中间层，客户只需点击"授权"按钮
- 14 天超级关怀期确保所有 OAuth 连接稳定运行
- 解决了 OpenClaw 最大的非技术用户上手障碍

在 Jesse Genet 的 [[案例-Jesse Genet 家庭教育系统|五 Agent 系统]] 中，每个 Agent 需要独立的 API 授权（iMessage、邮箱、银行只读 API 等），类似 Composio 的中间件使得这种多 Agent 多服务的授权管理成为可能。

## 关键洞察

Composio 揭示了 AI Agent 落地的一个隐藏瓶颈：**技术栈中最让非技术用户望而却步的不是 AI 本身，而是连接现有服务的授权流程**。OpenClaw 用 WhatsApp 解决了"界面门槛"，用 Ollama 解决了"成本门槛"，但 OAuth 配置仍然是一道横亘在 [[编程民主化]] 道路上的技术壁垒。Composio 类服务的出现，正在逐步填平这道鸿沟。这也是为什么围绕 OpenClaw 诞生了 SetupClaw、Clawable.ai、RemoteOpenClaw.com 等一系列 [[白手套部署服务]]——它们本质上都在解决授权配置问题。

## 外部链接

- [Composio 官方网站](https://composio.dev)
- [OAuth 2.0 规范](https://oauth.net/2/)

## 相关笔记

- [[白手套部署服务]] — Composio 是白手套服务商的核心技术栈
- [[编程民主化]] — OAuth 简化是编程民主化的一环
- [[非技术用户真实案例]] — 非技术用户如何跨越授权障碍
- [[可及性突破]] — Agent 可及性的技术栈分析
- [[学习曲线与上手门槛]] — OAuth 是上手门槛的关键因素
- [[OpenClaw 商业模式]] — 白手套服务是生态商业化的方向之一
