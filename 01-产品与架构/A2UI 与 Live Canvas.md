---
tags:
  - 架构
  - UI
  - OpenClaw
aliases:
  - A2UI
  - Agent-to-UI
  - Live Canvas
  - Canvas
---

# A2UI 与 Live Canvas

A2UI（Agent-to-UI）是由 Google 创建的**开源标准**（Apache 2.0 许可，当前 v0.8），定义了 AI Agent 如何向用户呈现声明式 UI——Agent 不只返回文本，还能渲染富交互界面。这是 Agent 范式转变在交互层面的重要体现。

## Canvas 架构

Canvas 运行在独立的服务器端口 18793，与 [[OpenClaw 是什么|OpenClaw]] Gateway（18789）分离。这种端口分离设计实现了**故障隔离**——Canvas 渲染服务崩溃不会影响核心 Agent 通信。

## 数据流

```
Agent 决策 -> canvas_update() -> WebSocket 推送 -> 浏览器渲染 UI 组件
```

Agent 通过 `canvas_update()` 函数声明 UI 变更，系统通过 WebSocket 实时推送到客户端渲染。这一过程是 [[Agent-Flow-Loop 原理|Agent Flow Loop]] 中 Phase 6 响应交付阶段的富媒体扩展。

## 多平台支持

| 平台 | 渲染技术 |
|------|----------|
| macOS | 原生 WKWebView |
| iOS | SwiftUI 包装 |
| Android | WebView |
| Web 浏览器 | 直接渲染 |

核心理念：Agent 只需声明"我想展示什么"，具体渲染由各平台原生实现适配。这是 [[Tool Use 机制]]在 UI 层面的延伸，也呼应了 MCP 协议标准化 Agent 与外部系统交互的理念。

## 与非技术用户的关系

Canvas 让 Agent 输出不再局限于纯文本，而是可以呈现交互式表格、图表和表单。这对非技术用户桌面应用和编程民主化至关重要——用户无需理解底层逻辑，直接通过可视化界面与 Agent 交互。[[Claude Code 的技术架构]] 中也有类似的富输出机制，但主要面向开发者。

## 相关笔记

- [[OpenClaw 是什么]]
- [[Agent Execution Loop]]
- [[Tool Use 机制]]
- [[System Prompt 设计]]

## 参考

- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
- [A2A Protocol - Google](https://github.com/google/A2A)
