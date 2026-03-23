---
tags:
  - 案例
  - 智能家居
  - HomeAssistant
  - 语音控制
  - OpenClaw
aliases:
  - Ken Bostrom
  - DIY家庭自动化
  - Home Assistant Agent
---

# 案例：Ken Bostrom DIY 家庭自动化

**一句话总结**：用 OpenClaw 连接 Home Assistant，通过自然语言和语音指令控制灯光、温度等智能家居设备，把技术门槛从"写 YAML 配置"降到"发消息"。

## 核心内容

[[ClawHub 技能市场|Skills 市场]] 中有 56 个智能家居 & IoT 类技能。@ngutman 率先在树莓派上部署 OpenClaw，通过自然语言控制智能家居。Ken Bostrom 等 DIY 爱好者跟进推广。

## 详细分析

### 技术架构

[[OpenClaw 是什么|OpenClaw]] 通过 [[Agent Flow Loop|Agent 执行循环]] 处理语音或文字指令，调用 Home Assistant API 控制设备：交互层（WhatsApp/Telegram/语音唤醒）→ 推理层（LLM 理解意图）→ 执行层（HA Skill 调用 API）→ 设备层（Zigbee/WiFi 设备）。

### 语音交互

- **Jupiter Voice**：Apple Silicon 本地语音助手，支持自定义唤醒词
- **ElevenLabs TTS**：高质量语音反馈
- 像跟 Siri 说话一样控制家居，但后端由 OpenClaw Agent 驱动

### 与传统方案的对比

| 维度 | 传统 HA | OpenClaw + HA |
|------|--------|---------------|
| 配置 | YAML / Node-RED | 自然语言 |
| 触发 | 预设条件 | 随时语音/消息 |
| 灵活性 | 需提前定义所有场景 | Agent 自主推理 |

## 关键洞察

体现了 [[编程民主化]] 在 IoT 领域的延伸。但需警惕 [[安全边界与风险（总览）|安全风险]]——家庭设备控制权暴露给 Agent 后，[[提示注入攻击]] 可能操纵物理设备。树莓派本地部署降低了攻击面，但 [[ClawHub 安全事件（ClawHavoc）|36.82% 的 Skills 存在漏洞]] 仍需关注。这是 [[Vibe Coding]] 式交互在硬件控制场景的典型应用。

## 来源

- [OpenClaw Showcase](https://docs.openclaw.ai/start/showcase)
- [awesome-openclaw-usecases](https://github.com/hesamsheikh/awesome-openclaw-usecases)
- [The Verge - Smart Home AI Agents](https://theverge.com)
- [Hacker News Discussion](https://news.ycombinator.com)
