---
tags:
  - 概念
  - 人物
  - Agent
aliases:
  - Claws
  - Karpathy Claws
---

# Karpathy 的 Claws 概念

## 什么是 Claws？

2026 年 2 月，Andrej Karpathy 在推特上发表了关于"Claws"的迷你论文：

> "I do love the concept... **Claws are now a new layer on top of LLM agents**, taking the orchestration, scheduling, context, tool calls and persistence to a next level."

"Claw"正在成为一个专业术语（term of art），指代 OpenClaw 类的 Agent 系统——运行在个人硬件上、通过消息协议通信、既能响应直接指令也能调度任务的 AI Agent。

## 技术栈的新抽象层

Karpathy 的洞察：**LLM Agent 之于 LLM，就像 Claws 之于 LLM Agent**：

```
LLM（语言模型） → LLM Agent（工具调用+推理循环） → Claw（编排+调度+持久化+消息接口）
```

每一层都是上一层的编排和增强。

## Simon Willison 的评价

> "Andrej has an ear for fresh terminology (see **vibe coding**, **agentic engineering**) and I think he's right about this one, too."

就像 Karpathy 创造的"vibe coding"被 Merriam-Webster 收录、成为 Collins 词典 2025 年度词汇一样，"Claws"有望成为 AI 技术栈中的持久术语。

## 对 OpenClaw 的安全顾虑

Karpathy 对运行 OpenClaw 表示谨慎：

> "I'm definitely a bit sus'd to run OpenClaw specifically — giving my private data/keys to **400K lines of vibe coded monster** that is being actively attacked at scale is not very appealing at all."

他推荐了更轻量的替代品，如 [[NanoClaw]]（核心引擎约 4,000 行代码，默认容器化运行）。

## 对 Moltbook 的评价

对 Moltbook（只有 AI Agent 可以发帖的社交网络）：

> **"genuinely the most incredible sci-fi takeoff-adjacent thing"**

但同时警告：

> **"a complete mess of a computer security nightmare at scale"**

Moltbook 5 天内声称 150 万 Agent 用户，但所有 Agent 的 API 密钥暴露在公开数据库中（详见 [[Moltbook 数据库泄露事件]]）——完美诠释了 Agent 领域的核心矛盾：**创新速度远超安全边界**。

## 整体评价

> "Claws are an awesome, exciting new layer of the AI stack."
> "Something aesthetically pleasing about there being a physical device 'possessed' by a little ghost of a personal digital house elf."

## 相关笔记

- [[Karpathy vs Altman Agent 元年之争]]
- [[Moltbook 数据库泄露事件]]
- [[Agent-Flow-Loop 原理]]
- [[OpenClaw 是什么]]
- [[安全边界与风险（总览）]]

## 外部链接

- [OpenAI](https://openai.com)
- [Anthropic](https://anthropic.com)
