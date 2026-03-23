---
title: Telegram Bot API
aliases: [Telegram Bot, Telegram 集成, grammY]
tags: [Telegram, Bot, API, channel, messaging, OpenClaw, Webhook]
created: 2026-03-15
updated: 2026-03-15
---

## 一句话总结

Telegram Bot API 是 OpenClaw 最容易上手的消息通道——免费创建 Bot、无需商业审批、原生支持流式输出，是官方推荐的第一个集成频道。

## 核心功能

Telegram Bot 平台托管超过 **1000 万个 Bot**，对用户和开发者完全免费。与 WhatsApp 需要商业 API 审批不同，Telegram 的入门成本为零：

| 维度 | Telegram | WhatsApp |
|------|----------|----------|
| 入门门槛 | 免费，几分钟搞定 | 需要商业 API 审批 |
| 流式输出 | 原生支持 | 不支持 |
| 文件大小 | 最大 2GB | 有限制 |
| 用户规模 | ~9 亿 | ~20 亿 |
| AI Bot 政策 | 完全开放 | 2026 年禁止通用 AI Bot |

创建流程：找 @BotFather → 发送 `/newbot` → 获取 Token → 配置到 OpenClaw → 完成。

Bot API 9.5（2026.3.1）重大更新：`sendMessageDraft` 方法支持流式响应，AI 回复可逐字显示；Mini Apps 支持全屏和手势；Telegram Stars 实现 Bot 变现。

## OpenClaw 中的应用

OpenClaw 通过 **grammY** 库（TypeScript Telegram Bot 框架）实现 Telegram 集成：

- `openclaw onboard` 向导**默认引导 Telegram** 作为第一个频道
- 支持群组中的多话题线程对话
- [[Webhook 技术]] 接收入站消息，[[消息路由]] 分发至对应 Agent
- 语音条支持：按住说话 → Whisper 转录 → Agent 处理 → Opus 48kHz/64kbps 语音回复

典型部署模式：Hetzner VPS（€5-7/月）+ Telegram Bot Token（免费）+ LLM API = 最低成本的 24/7 Agent。三个 AI 人格评测案例（Morty/Pepper Potts/David Goggins）就是基于这个架构。华尔街级股票筛选器通过三个 Telegram 命令（`oversold`、`screen`、`analyze`）操控整个系统。

## 关键洞察

Telegram 之所以成为 OpenClaw 最流行的频道，不仅因为免费和开放，更因为它的技术特性与 AI Agent 天然契合：流式响应让对话体验接近 ChatGPT 原生界面，2GB 文件传输支持大规模数据交互，线程机制让多 Agent 场景有序运行。WhatsApp 虽然用户更多（20 亿 vs 9 亿），但 2026 年对通用 AI Bot 的禁令使 Telegram 成为 [[多频道消息架构|OpenClaw 多频道策略]] 中事实上的首选。

## 外部链接

- [Telegram Bot API 官方文档](https://core.telegram.org/bots/api)

## 相关笔记

- [[多频道消息架构]] — Telegram 作为 Channel Adapter 之一
- [[消息路由]] — 入站消息的分发机制
- [[Webhook 技术]] — Bot 接收消息的技术方式
- [[WhatsApp Bot 集成]] — 与 Telegram 的对比
- [[ElevenLabs|ElevenLabs 语音集成]] — Telegram 语音条的 TTS 支持
- [[Discord Bot 集成]] — 另一个主流消息通道
