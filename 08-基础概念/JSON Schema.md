---
tags:
  - 基础概念
  - JSON
  - API
  - 工具定义
  - AI-Agent
aliases:
  - JSON Schema
  - JSON模式
  - 工具参数定义
---

# JSON Schema

**一句话总结**：JSON Schema 是描述 JSON 数据结构的标准格式，在 AI Agent 生态中扮演"工具说明书"的角色——它告诉 LLM 每个工具需要什么参数、什么类型、什么约束。

## 核心内容

JSON Schema 定义了一套词汇表用于注解和验证 JSON 文档。在 AI Agent 领域，它是 [[Tool Use 机制|工具调用]] 的基础语言——LLM 通过阅读 JSON Schema 理解一个工具能做什么、接受什么输入。

## 详细分析

### 在 AI Agent 中的核心作用

| 环节 | JSON Schema 的角色 |
|------|-------------------|
| **工具注册** | 定义每个工具的参数格式和约束 |
| **LLM 推理** | 模型根据 Schema 生成合法的工具调用参数 |
| **运行时验证** | 拦截不合法的工具调用，防止参数注入 |
| **API 对接** | 标准化 Agent 与外部服务的接口契约 |

### OpenClaw 中的实践

[[OpenClaw 是什么|OpenClaw]] 使用 TypeBox 库同时提供 TypeScript 类型推导和 JSON Schema 验证。[[TypeBox Schema 工具定义]]在 OpenClaw 中实现了 JSON Schema 的编译期 + 运行时双重验证——这是理论到工程实践的典型落地。TypeBox 编译时生成类型定义，运行时自动验证输入——确保 Agent 调用工具时参数符合预期。

### 各厂商实现

Anthropic（Tool Use）、OpenAI（Function Calling，strict mode 要求完全符合）、Google（Function Declarations）均基于 JSON Schema 定义工具接口。[[MCP（Model Context Protocol）]] 也使用 JSON Schema 定义 Tools、Resources 和 Prompts 的接口规范，使不同 Agent 框架可共享工具生态。

## 关键洞察

JSON Schema 在 AI Agent 领域的重要性常被低估。它不仅是"数据格式"，更是 LLM 与外部世界交互的 [[安全边界与风险（总览）|安全边界]] 之一。严格的 Schema 验证可防止 LLM 幻觉导致的无效工具调用，也能缓解 [[提示注入攻击]]——恶意指令即使诱导 LLM 调用工具，也必须通过 Schema 验证这道关卡。对 [[ClawHub 技能市场|Skills 开发者]] 而言，良好的 Schema 定义直接影响 Agent 调用该 Skill 的准确率。

## 来源

- [JSON Schema 官方规范](https://json-schema.org/)
- [OpenClaw 架构文档 - DeepWiki](https://deepwiki.com/openclaw/openclaw/15.1-architecture-deep-dive)
- [Anthropic Tool Use 文档](https://docs.anthropic.com/en/docs/tool-use)
