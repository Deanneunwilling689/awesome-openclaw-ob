---
title: ElevenLabs
aliases: [ElevenLabs TTS, 语音合成, ElevenLabs TTS 集成, OpenClaw 语音, TTS 集成, ElevenLabs 语音集成]
category: 技术生态
tags: [TTS, voice, speech-synthesis, ElevenLabs, audio, Opus, 语音合成, OpenClaw]
created: 2026-03-14
updated: 2026-03-14
---

## ElevenLabs 公司和产品

ElevenLabs 是一家专注于 AI 语音技术的公司，愿景是"让技术与人的沟通无缝衔接"。他们从语音合成（TTS）起步，现已扩展到语音克隆、音效生成、语音转录（Scribe）等领域。

核心产品线：
- **Text-to-Speech**：支持 70+ 语言、32 种语言的高质量合成
- **Voice Cloning**：几分钟音频即可复制任何人的声音（需授权验证）
- **Scribe v2**（2026年1月发布）：号称"最准确的转录模型"
- **Conversational AI 2.0**：端到端低于 100ms 延迟的实时对话

用一句话概括：**ElevenLabs 把"文字变声音"这件事，做到了人类几乎分辨不出真假的水平。**

## 语音合成技术原理

传统 TTS 像拼图——从语音库里找音素拼接，听起来机械。ElevenLabs 的方法是端到端神经网络生成：模型直接从文本生成音频波形，自带语调、节奏、情感。

关键模型演进：
- **Multilingual V2**：29种语言，情感表达最稳定
- **Flash V2.5**：75ms 超低延迟，适合实时对话，成本低50%
- **V3**（最新）：表达力最强，但偶有不稳定

## 在 OpenClaw 中的集成

[[OpenClaw 是什么|OpenClaw]] 的 TTS 配置在 `openclaw.json` 的 `messages.tts` 下，支持三种引擎：

| 引擎 | 特点 | 成本 |
|------|------|------|
| Edge TTS | 默认启用，微软引擎 | 免费 |
| OpenAI TTS | 质量好，延迟中等 | 按字符计费 |
| **ElevenLabs** | 最自然，支持克隆 | 按字符计费 |

OpenClaw 生态中的语音方案：
1. **内置 TTS**：在 `openclaw.json` 中配置 `voiceId`、`modelId` 即可
2. **OpenClaw Voice**（浏览器端）：Whisper 本地转录 + ElevenLabs 流式合成，逐句播放
3. **VoxClaw**（Mac 菜单栏）：让远程 OpenClaw 通过局域网在 Mac 上朗读
4. **电话呼叫**：通过 ElevenLabs Agents + Twilio/Plivo 实现真实电话交互
5. **Telegram 语音条**：按住说话 → 转录 → 处理 → Opus 格式 48kHz/64kbps 语音回复，全程语音

社区还开发了支持 30+ 语言（含普通话和粤语）的语言学习 Skill。

## 语音交互对 Agent 体验的影响

语音不只是"换个输出形式"。当 Agent 能听、能说：
- **交互门槛归零**：不会打字的老人也能使用 AI Agent（推动 [[编程民主化]]）
- **情感维度增加**：声音的语调传递信任感，文字做不到
- **场景解锁**：开车、做饭、健身时也能与 Agent 对话
- **从工具到伙伴**：有声音的 Agent 更像"一个人"而非"一个软件"
- **多频道扩展**：让 [[多频道消息架构|多频道架构]] 的触达范围从"会打字的人"扩展到"所有人"

## 外部链接

- [ElevenLabs 官方网站](https://elevenlabs.io)

## 相关笔记

- [[OpenClaw 语音交互]] —— OpenClaw 语音功能的完整生态
- [[编程民主化]] —— 语音交互降低使用门槛
- [[非技术用户真实案例]] —— 语音场景的实际应用
- [[多频道消息架构]] —— 语音作为消息通道之一
- [[Telegram Bot API]] —— Telegram 原生支持 Opus 语音
- [[模型无关架构]] —— TTS 引擎也可自由切换
