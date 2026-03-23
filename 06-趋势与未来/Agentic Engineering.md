---
tags:
  - Karpathy
  - Agentic Engineering
  - Vibe-Coding
  - 范式转变
  - Agent
aliases:
  - Agentic Engineering
  - 编排 Agent
  - Karpathy 一周年回顾
---

# Agentic Engineering

## 一句话总结

> 从"写代码"到"编排 Agent"——Karpathy 在 vibe coding 一周年时提出的升级概念：未来软件工程不是敲键盘，而是设计、调度和监督一群 AI Agent 替你工作。

## 核心内容

2026 年 2 月，Andrej Karpathy 在 vibe coding 一周年回顾中提出 **"agentic engineering"**："**agentic** 因为新的默认方式是编排 Agent 而非直接写代码，**engineering** 强调其中涉及的艺术、科学和专业知识。"

## 详细分析

**从 Vibe Coding 到 Agentic Engineering**：Vibe Coding（2025.2）是"forget that the code even exists"的随性风格，获得 450 万+浏览量并成为 Collins 词典 2025 年度词汇。Karpathy 自嘲那是"a shower of thoughts throwaway tweet"。Agentic Engineering 则是有意识地设计 Agent 工作流，强调专业性。

**技术栈层级**（源自 [[Karpathy 的 Claws 概念|Claws]] 论述）：`LLM → LLM Agent（工具调用+推理） → Claw（编排+调度+持久化+消息接口）`。Agentic Engineer 在最上层工作：设计 Agent 角色分工、编排通信协作、设置安全边界、监督执行质量。

**实践者**：[[Peter Steinberger]] 同时运行 3-4 个 AI Agent，用语音输入驱动，"Prompt Requests" 替代 Pull Requests，一个月 6,600+ commits。他自嘲："I do agentic engineering... maybe after 3am I switch to vibe coding, then have regrets."

**Simon Willison** 评价："Andrej has an ear for fresh terminology and I think he's right about this one, too."

## 关键洞察

编程正从"实现"变成"管理"——核心技能从写代码上移到设计 Agent 工作流。但结合 [[半人马阶段理论|Amodei 的警告]]，这个技能本身的保质期可能也有限：当 Agent 能力再上一个台阶，"编排 Agent"本身也可能被 Agent 接管。

- [[Karpathy 的 Claws 概念]] | [[Karpathy vs Altman Agent 元年之争]] | [[半人马阶段理论]] | [[Agent 范式转变]] | [[2026 Agent 元年]]

## 外部链接

- [Anthropic](https://anthropic.com)
- [OpenAI](https://openai.com)

> 来源：[Karpathy 一周年](https://x.com/karpathy/status/2019137879310836075) | [Simon Willison](https://simonwillison.net/2026/Feb/21/claws/) | [Lex Fridman #491](https://lexfridman.com/peter-steinberger-transcript/)
