---
title: Transformer 架构
aliases: [Transformer, 注意力机制, Self-Attention, 自注意力]
tags: [Transformer, 深度学习, NLP, 注意力机制, 神经网络, LLM]
created: 2026-03-15
updated: 2026-03-15
---

## 一句话总结

Transformer 是 2017 年 Google 提出的神经网络架构，用"自注意力机制"让模型同时看到整个输入序列中每个词之间的关系——它是从 GPT 到 Claude 到 DeepSeek 所有现代大语言模型的共同基础。

## 核心功能

Transformer 的核心是**自注意力（Self-Attention）**：

- **Query（查询）**：我在找什么关联？
- **Key（键）**：我能提供什么信息？
- **Value（值）**：我实际的内容是什么？

每个词生成 Q/K/V 三个向量，通过点积计算注意力分数，Softmax 归一化后加权求和。**多头注意力**让模型同时从语法、语义、位置等多个角度分析词间关系。

与 RNN/LSTM 的关键差异：

| 特性 | RNN/LSTM | Transformer |
|------|----------|-------------|
| 处理方式 | 逐步顺序 | 并行处理 |
| 长距离依赖 | 梯度消失 | 直接注意力连接 |
| 训练速度 | 慢 | 快（高度并行化） |
| 可扩展性 | 有限 | 极强（Scaling Laws） |

## OpenClaw 中的应用

OpenClaw 的 [[模型无关架构]] 让它可以接入任何基于 Transformer 的 LLM：

- **Anthropic Claude 系列**（Opus 4.6 SWE-bench 80.8%）：原生流式、200K 上下文
- **OpenAI GPT 系列**（GPT-5.3 Codex）：Function Calling、Terminal-Bench 77.3%
- **DeepSeek V3/R1**：MoE 架构 + Multi-head Latent Attention 创新
- **Google Gemini 3.1 Pro**：ARC-AGI-2 77.1%，成本仅为 Opus 的 1/7.5
- **本地模型**：通过 [[Ollama 本地模型运行|Ollama]] 运行 Llama、Qwen 等开源 Transformer 模型

2026 年 2 月，16 天内三大前沿模型发布（Opus 4.6、GPT-5.3、Gemini 3.1），SWE-Bench 差距不到 1 个百分点——Transformer 架构的 Scaling Laws 已接近当前范式的天花板。Scaling Laws 决定了[[2026 前沿模型竞争格局]]的本质是资本竞争——谁能堆更多算力、喂更多数据，谁就领先那不到 1% 的差距。

## 关键洞察

Transformer 的真正革命性在于**可扩展性**——堆叠更多层 + 更多数据 = 更强能力，这个简单规律（Scaling Laws）催生了整个 LLM 产业。从 2017 年 "Attention Is All You Need" 论文到 2026 年 OpenClaw 连接数十个 Transformer 模型，这个架构已经从学术论文变成了全球 AI 基础设施。DeepSeek 的 MLA（Multi-head Latent Attention）是对原版注意力机制的重要改进，大幅降低了 KV 缓存内存占用，让更大的模型在更少的硬件上运行成为可能。

## 相关笔记

- [[大语言模型]] — Transformer 是所有现代 LLM 的底层架构
- [[Claude 模型系列]] — Claude 基于 Transformer 构建
- [[GPT 模型系列]] — GPT 使用 Transformer 解码器架构
- [[DeepSeek]] — MoE + MLA 对 Transformer 的创新改进
- [[向量嵌入与混合搜索]] — 嵌入向量由 Transformer 模型生成
- [[模型无关架构]] — OpenClaw 抽象了 Transformer 模型的差异
- [[提示工程]] — 理解注意力机制有助于设计更好的提示
