---
tags:
  - 语音
  - 功能
  - OpenClaw
aliases:
  - TTS
  - 语音助手
---

# OpenClaw 语音交互

OpenClaw 支持多种语音交互方式，进一步降低使用门槛。

## 文字转语音（TTS）

- **ElevenLabs** 原生 TTS 支持，实现高质量语音输出
- Telegram 支持 **Opus 语音格式**（48kHz / 64kbps），语音消息清晰自然

## 语言学习 Skill

社区开发的语言学习技能：
- 支持 **30+ 主要语言**，包括普通话和粤语
- 用户通过语音对话练习外语，AI 实时纠正发音和语法
- 这类技能通过 ClawHub 发布，借助 [[Tool Use 机制]] 与外部语音 API 交互

详见 [[Skills 市场]]。

## Jupiter Voice

- **Apple Silicon 本地语音助手**
- 支持自定义唤醒词
- 在 Mac 上实现类似 Siri 的体验，但后端由 [[OpenClaw 是什么|OpenClaw]] Agent 驱动
- 通过 LLM 理解自然语言指令，结合自主决策循环执行复杂任务

## 意义

语音交互是编程民主化的进一步延伸——连文字输入都不需要，直接用语音与 AI Agent 对话。这也是可及性突破的重要组成部分。

## 相关笔记

- [[OpenClaw 是什么]]
- [[Tool Use 机制]]
- [[Skills 市场]]

## 参考

- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
- [ElevenLabs](https://elevenlabs.io)
