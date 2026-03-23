---
title: GPT 模型系列
aliases: [GPT, OpenAI GPT, ChatGPT]
category: 模型分析
created: 2026-03-14
updated: 2026-03-14
tags: [OpenAI, GPT, LLM, ChatGPT]
---

# GPT 模型系列

> **一句话本质：** GPT（Generative Pre-trained Transformer）是 OpenAI 的旗舰大语言模型系列，从"能写文章的玩具"进化为"能操作电脑的全能智能体"，是当前商业化最成功的 LLM 家族。

## 演进时间线

| 版本 | 时间 | 里程碑意义 |
|------|------|-----------|
| GPT-3 | 2020.06 | 175B 参数，证明 scaling law |
| GPT-3.5 | 2022.11 | ChatGPT 发布，AI 出圈 |
| GPT-4 | 2023.03 | 多模态，通过律师/医生考试 |
| GPT-4o | 2024.05 | 原生多模态，语音实时对话 |
| GPT-5 | 2025 中 | 统一推理与生成，性能大幅提升 |
| GPT-5.2 | 2025 末 | 推理错误和幻觉显著减少，开源 gpt-oss-120b |
| GPT-5.3 Instant | 2026.03.03 | 400K 上下文，幻觉再降26.8% |
| GPT-5.4 | 2026.03.05 | 1M 上下文，原生 Computer Use，5级推理深度 |

## GPT-5.4：当前最新旗舰

GPT-5.4 是截至2026年3月 OpenAI 最强模型，关键能力：

- **1M token 上下文窗口**：可一次分析完整代码库或大型文档集
- **可配置推理深度**：none / low / medium / high / xhigh 五档，按需平衡速度与质量
- **原生 Computer Use**：首个通用模型支持操作电脑执行复杂工作流
- **GDPval 基准**：在44个职业的知识工作评测中，83.0%的对比中达到或超过人类专家水平

### GPT-5.4 Pro

为 Pro/Enterprise 用户提供的增强版，使用更多计算资源进行深度推理，适合最高难度任务。

## 定价与经济性

GPT-5.4 输出 token 成本约为 Claude Opus 4.6 的 40%，在性能相当的前提下，大规模部署经济优势明显。这改变了前沿模型的成本格局（详见 [[API 定价与成本分析]]）。

## 开源动作

OpenAI 发布了 **gpt-oss-120b**——117B 参数的 MoE 架构模型，MIT 许可证，性能接近 o4-mini。这是 OpenAI 在开源领域的重大转向，回应了 [[DeepSeek]] 等开源模型的竞争压力。

## 在 OpenClaw 中的集成

[[OpenClaw 是什么]] 通过 [[模型无关架构]] 支持 GPT 系列：

- GPT-5.4 适合需要 Computer Use 的桌面自动化场景
- GPT-5.3 Instant 适合高频低延迟的批量任务
- 通过统一的 API 抽象层切换，无需改动 Agent 逻辑
- 与 MCP 协议兼容的工具调用格式

## 遗留与淘汰

GPT-4o、GPT-4、GPT-3.5 正在逐步淘汰。GPT-5.2 Thinking 将于 2026年6月5日退役。建议新项目直接使用 GPT-5.4。

## 延伸阅读

- [[DeepSeek]] — 开源竞争对手
