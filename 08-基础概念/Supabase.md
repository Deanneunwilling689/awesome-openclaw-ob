---
title: Supabase
aliases: [Supabase BaaS, 开源 Firebase 替代]
tags: [Supabase, BaaS, PostgreSQL, RLS, Moltbook, 数据泄露, 安全]
created: 2026-03-15
updated: 2026-03-15
---

## 一句话总结

Supabase 是开源的 Firebase 替代品，基于 PostgreSQL 提供数据库、认证和存储服务——但 Moltbook 因 Supabase 配置错误（缺失 RLS 行级安全策略），导致 150 万 API 令牌和 35,000 用户邮箱泄露。

## 核心功能

Supabase 提供一站式后端即服务（BaaS）：
- **PostgreSQL 数据库**：全功能关系型数据库，支持 Row Level Security（RLS）
- **认证**：内置用户注册/登录、OAuth 社交登录
- **存储**：文件存储与 CDN 分发
- **实时订阅**：数据变更实时推送到客户端
- **Edge Functions**：无服务器函数

关键安全特性 **RLS（Row Level Security）**：数据库级别的访问控制策略，确保用户只能访问自己有权限的数据行。不启用 RLS 意味着客户端可以直接读写所有数据。

## OpenClaw 中的应用

Supabase 本身不是 OpenClaw 的组件（OpenClaw 使用 [[SQLite 数据存储|SQLite]]），但 **Moltbook 数据泄露事件** 是 OpenClaw 安全叙事中最重要的案例之一：

**事件经过（2026.1.31）**：
- Wiz 研究团队发现 AI 社交网络 Moltbook 的 Supabase **缺失 RLS 策略**
- 客户端 JavaScript 中**硬编码 Supabase 凭证**
- 暴露数据：~150 万 API 令牌、~35,000 邮箱、4,060 条私信（含明文 OpenAI API 密钥）
- 创始人 Matt Schlicht 公开承认"没有亲手写过一行代码"，全部 AI 生成
- 声称 150 万"AI agents"，实际仅约 17,000 个人类账户（**88:1 比例**）
- Wiz 通知后 **3.5 小时内修复**

这个事件是 [[Vibe Coding]] 风险的经典案例——AI 生成的代码可能跳过安全最佳实践（如启用 RLS），开发者不审查代码则无法发现问题。

## 关键洞察

Moltbook 事件不是 Supabase 的问题——Supabase 提供了 RLS，是使用者没有启用。这暴露了 AI Agent 生态的一个深层隐患：当 [[编程民主化]] 让不懂安全的人也能快速构建产品时，谁来负责安全配置？Moltbook 的教训是：**Vibe Coding 可以生成功能正确的代码，但安全性需要人类专业知识把关**。这也是为什么 [[安全厂商评估汇总|安全厂商]] 普遍对 OpenClaw 生态表示担忧——不是框架本身不安全，而是生态中的快速构建文化系统性地低估了安全配置的重要性。

## 外部链接

- [Supabase 官方网站](https://supabase.com)

## 相关笔记

- [[SQLite|SQLite 数据存储]] — OpenClaw 自身使用 SQLite 而非 Supabase
- [[ClawHub 安全整改措施]] — Moltbook 事件推动的安全整改
- [[Vibe Coding]] — AI 生成代码的安全隐患
- [[致命三合一安全矛盾]] — Agent 生态的根本安全挑战
- [[编程民主化]] — 降低编程门槛的安全代价
- [[安全厂商评估汇总]] — 各厂商对 Agent 安全的评价
