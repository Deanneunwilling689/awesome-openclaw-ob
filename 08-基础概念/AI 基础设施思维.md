---
title: AI 基础设施思维
aliases: [Infrastructure Thinking, 基础设施层]
tags: [concept, infrastructure, paradigm, feynman]
created: 2026-03-14
updated: 2026-03-14
sources:
  - https://www.madrona.com/ai-agent-infrastructure-three-layers-tools-data-orchestration/
  - https://www.ibm.com/think/topics/agentic-architecture
  - https://www.quali.com/blog/agentic-layers-the-architecture-behind-autonomous-infrastructure/
  - https://dzone.com/articles/ai-infrastructure-agents-llms-tools-optimization
---

## "基础设施问题"是什么意思

用费曼的方式想：大多数人看到 AI 的第一反应是"怎么写更好的 prompt"。这就像看到一台发动机，想的是"怎么给它加更好的油"。

**基础设施思维**换了个角度：先别管油，我们需要造一辆车。发动机再好，没有方向盘、刹车、底盘，它就只是个噪音很大的铁块。

所以真正的问题不是"如何更好地使用 LLM"，而是**"如何围绕 LLM 构建一整套可靠的系统"**。

## LLM 是引擎，框架是汽车

这个比喻精确地抓住了本质：

- **LLM（引擎）**：提供原始智能——理解语言、推理、生成内容
- **Agent 框架（汽车）**：提供结构——工具调用、记忆管理、权限控制、错误恢复、任务编排

引擎再猛，没有传动系统就跑不了。同样，GPT-4o 再聪明，没有框架就只能聊天，不能做事。

## 2026 年的 AI 基础设施分层

现代 Agent 基础设施由三大支柱组成（Madrona 框架）：

| 层 | 职责 | 类比 |
|----|------|------|
| **工具层** | Agent 如何与外部世界交互（[[MCP 协议]] 正成为标准） | 手和脚 |
| **数据层** | Agent 如何获取和存储信息 | 记忆和知识 |
| **编排层** | Agent 如何规划、执行、协调多步骤任务 | 大脑的执行功能 |

## OpenClaw 的操作系统层定位

OpenClaw 把自己定位为 **Agent 的操作系统**，而不是一个应用。它不做某一件具体的事，而是提供一个平台，让任何 Skill 都能在上面运行。就像 iOS 本身不发消息，但 iMessage 在它上面跑。

这个定位意味着：OpenClaw 解决的不是"某个任务怎么自动化"，而是"所有任务的自动化需要什么底层能力"——记忆、工具调用、权限、安全沙箱、[[模型无关架构|多模型支持]]。

## 与"提示工程"思维的本质区别

| 提示工程思维 | 基础设施思维 |
|-------------|-------------|
| "怎么写更好的 prompt" | "怎么构建更好的系统" |
| 优化单次交互 | 优化持续运行的流程 |
| 依赖一个模型的能力 | 模型无关，可替换引擎 |
| 用户需要专业知识 | 系统替用户处理复杂性 |

## 为什么这个视角改变了一切

当你用基础设施思维看 AI，你就不再被单个模型的能力绑架。GPT-5 出来了？换个引擎。Claude 更便宜了？切过去。**真正的护城河不在模型，在基础设施。**

这也是为什么 OpenClaw 能做到"[[模型无关架构|模型无关]]"——因为它一开始就没把自己当成某个 LLM 的皮肤，而是当成一个操作系统。这种思维也解释了 AAIF 基金会为什么要标准化 Agent 基础设施——只有基础设施层统一了，上层应用才能繁荣。

---

**相关笔记：** [[OpenClaw 是什么]] | [[模型无关架构]] | [[MCP 协议]] | [[Agent Execution Loop]]
