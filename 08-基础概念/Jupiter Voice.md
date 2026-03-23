---
tags:
  - 语音
  - 智能家居
  - 硬件
  - IoT
aliases:
  - Jupiter Voice
  - Jupiter 语音
---

# Jupiter Voice

Jupiter Voice 是一款针对本地 AI Agent 场景的语音交互方案，可配合树莓派等设备在本地运行，为 [[OpenClaw 是什么|OpenClaw]] 提供类 Siri 的语音唤醒和对话体验。

## 应用场景

结合 [[Home Assistant 集成]]，Jupiter Voice 可以作为智能家居的语音前端：

- 用户通过语音发出自然语言指令
- 语音被转录后交由 OpenClaw Agent 处理
- Agent 调用 Home Assistant API 控制设备
- 配合 [[OpenClaw 语音交互|ElevenLabs TTS]] 实现语音回复

## 与传统语音助手的区别

传统语音助手（Siri、Alexa）依赖云端处理和固定模板命令。Jupiter Voice + OpenClaw 的组合完全本地运行，支持上下文理解和自然语言推理，隐私数据不离开本地设备。

## 相关笔记

- [[Home Assistant 集成]] — 智能家居控制平台
- [[OpenClaw 语音交互]] — OpenClaw 的语音技术栈
- [[Skills 市场]] — 智能家居类 Skills 分发
- [[Mac Mini 全球短缺现象]] — 本地 AI 硬件需求的表征
