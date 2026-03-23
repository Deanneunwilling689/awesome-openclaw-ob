---
tags:
  - Agent
  - 替代方案
  - 安全
  - 轻量化
aliases:
  - NanoClaw
  - Nano Claw
---

# NanoClaw

NanoClaw 是一个轻量级的 AI Agent 框架，核心引擎约 **4,000 行代码**，默认以容器化方式运行。[[Andrej Karpathy|Karpathy]] 在对 [[OpenClaw 是什么|OpenClaw]] 表达安全顾虑时推荐了它作为替代品。

## 与 OpenClaw 的对比

| 维度 | NanoClaw | OpenClaw |
|------|----------|----------|
| 代码规模 | ~4,000 行 | 400,000+ 行 |
| 默认隔离 | 容器化运行 | 主机直接运行 |
| 攻击面 | 极小 | 极大 |
| 功能丰富度 | 基础 Agent 能力 | 完整生态系统 |

## 为什么重要

Karpathy 不愿将私人数据交给 "400K lines of vibe coded monster"，NanoClaw 的设计理念正是**最小化攻击面**——代码越少，漏洞越少；默认容器化，即使出问题也限制了影响范围。

这体现了 [[安全边界与风险（总览）|AI Agent 安全]] 领域中"最小权限原则"的实践：功能够用即可，不需要为了灵活性牺牲安全性。

## 最新进展

2026 年 3 月 13 日，NanoClaw 创始人 Gavriel Cohen 宣布与 Docker 达成合作，从 Hacker News 发布到达成合作仅用 6 周。详见 [[NanoClaw 与 Docker 合作]]。

## 相关笔记

- [[NanoClaw 与 Docker 合作]] — 2026 年 3 月与 Docker 的合作详情
- [[Karpathy 的 Claws 概念]] — Karpathy 推荐 NanoClaw 的上下文
- [[OpenClaw 是什么]] — NanoClaw 的对比对象
- [[Docker 容器化]] — NanoClaw 默认采用的隔离方式
- [[安全边界与风险（总览）]] — Agent 安全的整体视角
