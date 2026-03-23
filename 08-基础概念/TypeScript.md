---
title: TypeScript
aliases: [TS, TypeScript语言]
tags: [概念, 编程语言, 技术栈]
created: 2026-03-14
updated: 2026-03-14
type: atomic-note
---

# TypeScript

## 一句话解释

TypeScript 就是给 JavaScript 穿上盔甲——你写的还是 JavaScript，但编译器会在你出错之前告诉你"这里类型不对"，防止一大类 bug 在运行时才炸开。

## 它到底是什么

TypeScript 是微软开发的 JavaScript 超集。"超集"意味着所有合法的JS代码也是合法的TS代码，但TS额外提供了**静态类型系统**。就像给一座大楼加了脚手架——建好之后脚手架（类型注解）会被拆掉（编译为纯JS），但施工过程中它能防止工人（开发者）从楼上摔下来。

## 为什么 OpenClaw 选择 TypeScript

[[OpenClaw 是什么|OpenClaw]] 用 TypeScript + Swift 编写，选择TS有几个关键理由：

1. **类型安全对Agent至关重要** — Agent会调用外部API、解析JSON、操作文件系统。没有类型检查，一个 `undefined` 就可能让整个工作流崩溃。类型系统把这类错误从"运行时炸弹"变成"编译时红线"，这对 [[Tool Use 机制]] 尤为关键
2. **前后端统一** — Agent的后端逻辑和前端UI可以用同一种语言写，减少上下文切换
3. **npm生态加持** — 通过 [[npm 生态系统]]，OpenClaw可以直接复用数百万个JS/TS包
4. **开发者基数最大** — GitHub 2025语言报告中，TypeScript正式超越Python成为最活跃语言

## 在AI工具生态中的地位

2026年，TypeScript已经成为AI Agent开发的主流选择之一：

- **YC X25** 批次中，60-70%的Agent创业公司选择TypeScript作为交付层
- **Vercel AI SDK** — 最受欢迎的TS AI框架，流式优先
- **Mastra** — 从零为TS生态设计的Agent框架
- **OpenAI Agents SDK** — 官方TS SDK，代码优先的Agent编排
- **Google ADK** — Agent Development Kit的TS版本
- **[[Claude Code 的技术架构|Claude Code]]** — Anthropic的官方CLI工具，同样使用TypeScript

关键趋势：Python仍然统治模型训练和ML研究，但**围绕AI的一切**——Agent、工作流、UX、胶水代码——正在快速迁向TypeScript。

## 类型安全为什么对Agent特别重要

想象一个Agent要连续执行5个步骤：查询数据库 → 解析结果 → 调用API → 格式化输出 → 发送消息。如果第2步返回了一个意外的数据结构，没有类型检查的话，错误会一路传播到第5步才爆炸，而且错误信息完全不知所云。

TypeScript的类型系统让每一步的输入输出都有明确的"合同"，任何一步违约，编译器立刻告警。这对多步骤、自主决策的 Agent 来说不是锦上添花，而是**生存必需品**。

## 外部链接

- [TypeScript 官方网站](https://typescriptlang.org)

## 双链

- [[OpenClaw 是什么]]
- [[npm 生态系统]]
- [[Skills 市场]]
- [[Tool Use 机制]]
