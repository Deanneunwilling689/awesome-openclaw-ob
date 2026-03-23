---
title: Ollama 本地模型运行
aliases: [Ollama, 本地 LLM, 离线模型运行]
tags: [Ollama, 本地部署, LLM, 离线, 隐私, OpenClaw]
created: 2026-03-15
updated: 2026-03-15
---

## 一句话总结

Ollama 让你在自己的电脑上运行大语言模型，无需 API Key、无需联网、零成本——是 OpenClaw 实现"完全离线 AI Agent"的关键基础设施。

## 核心功能

Ollama 是一个本地 LLM 运行时，将开源大模型的部署简化为一条命令。它解决了本地模型运行的三大痛点：模型下载、量化适配、推理服务。

关键特性：
- **零 API 成本**：模型运行在本地，不消耗任何云端 API 额度
- **完全离线**：下载模型后断网也能使用，数据永不离开设备
- **硬件依赖**：需要足够的 RAM/VRAM，推荐 Apple Silicon Mac 或 NVIDIA GPU
- **模型生态**：支持 Llama、Qwen、Mistral、DeepSeek 等主流开源模型

## OpenClaw 中的应用

OpenClaw 的 [[模型无关架构]] 将 Ollama 作为 Provider 之一集成到 LLM 层：

| 配置 | 月费 | 说明 |
|------|------|------|
| **纯本地 Ollama** | **$0** | 零 API 成本，性能受限于硬件 |
| 经济配置 | $13-18 | DeepSeek/小模型 API 混合 |
| 中端配置 | $5-15 | Claude Sonnet 按量计费 |

MFS Corp 案例是 Ollama 的最佳实践：6 个自主 Agent 运行在 Proxmox 上（48 核、503GB RAM），大部分推理交给本地 Ollama，月成本仅约 **$50**——这是"零人类员工 AI 公司"的成本秘密。

Reddit r/LocalLLaMA 社区中，Ollama + OpenClaw 的离线部署讨论是最热门话题之一。中国用户也积极使用 Kimi 2.5 等国产模型通过 Ollama 接入 OpenClaw。

## 关键洞察

Ollama 的价值不仅是省钱。它代表了 AI Agent 的一个根本性选择：**数据主权**。当你的 Agent 管理邮件、日历、财务信息时，数据是否离开设备是一个核心隐私问题。Ollama 让 OpenClaw 的 [[SQLite 数据存储|本地优先架构]] 真正闭环——数据存在本地 SQLite，推理也在本地完成。代价是推理能力受限于硬件，但对于日常任务，7B-14B 参数的量化模型已经"够用"。

## 外部链接

- [Ollama 官方网站](https://ollama.com)

## 相关笔记

- [[模型无关架构]] — Ollama 是 OpenClaw 支持的 Provider 之一
- [[DeepSeek]] — 通过 Ollama 可本地运行 DeepSeek 开源模型
- [[SQLite|SQLite 数据存储]] — 本地存储 + 本地推理 = 完全离线方案
- [[大语言模型]] — Ollama 运行的模型类型与能力
- [[开源AI运动]] — Ollama 是开源 AI 生态的重要基础设施
- [[竞品成本对比]] — Ollama 零成本方案的竞争力
