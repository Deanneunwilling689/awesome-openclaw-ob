---
tags:
  - 基础概念
  - WebSocket
  - 实时通信
  - 网络协议
  - 安全
aliases:
  - WebSocket
  - WS协议
  - 全双工通信
---

# WebSocket 协议

**一句话总结**：WebSocket 是 HTTP 之上的全双工通信协议，一次握手后双方可随时互发消息——它是 OpenClaw 实时交互的基础，也是 ClawJacked 漏洞的攻击面。

## 核心内容

传统 HTTP 是"请求-响应"模式。WebSocket 打破这个限制：连接建立后服务器可主动推送，客户端也可随时发送，实现真正的双向实时通信。

## 详细分析

### OpenClaw 中的 WebSocket 应用

[[OpenClaw 是什么|OpenClaw]] 的 Gateway 核心就是一个 WebSocket 服务器（默认 `ws://127.0.0.1:18789`）：

| 组件 | 用途 |
|------|------|
| Channel Adapters → Gateway | 消息路由 |
| Gateway → 客户端 | LLM Token 实时推送 |
| [[A2UI 与 Live Canvas|A2UI]] Canvas | UI 实时更新 |
| Heartbeat | 30 秒心跳保活 |

Gateway 复用同一端口承载 WebSocket + HTTP REST API + Control UI，使用指数退避重连。

### ClawJacked 漏洞（CVE-2026-25253）

WebSocket 的 CSWSH 漏洞正是 [[CVE-2026-25253 ClawJacked 漏洞详解]] 的攻击面。CVSS 8.8 漏洞利用**跨站 WebSocket 劫持（CSWSH）**：恶意网页 JS 向 localhost 发起 WebSocket 连接（绕过同源策略）→ 暴力破解密码（localhost 豁免速率限制）→ 窃取 Token → 完全控制 Gateway。关键问题：**WebSocket 不受浏览器同源策略保护**。修复方案（v2026.2.25+）：TOFU 策略 + Origin 头验证，24 小时内完成。

## 关键洞察

WebSocket 是 [[Agent Flow Loop|Agent 执行循环]] 的通信骨架。但其安全特性（不受同源策略限制）在本地部署场景下成为致命弱点。[[安全边界与风险（总览）|Diana Kelley（Noma Security CISO）]]："'本地'并不自动意味着'安全'。"这个教训超越 OpenClaw——任何绑定 localhost 的 WebSocket 服务都可能面临 CSWSH 攻击。[[Chrome DevTools Protocol]] 同样基于 WebSocket，因此 OpenClaw 的浏览器控制功能也继承了这层 [[ClawJacked 漏洞|攻击面]]。

## 外部链接

- [WebSocket API - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)

## 来源

- [RFC 6455 - The WebSocket Protocol](https://datatracker.ietf.org/doc/html/rfc6455)
- [The Hacker News - ClawJacked RCE](https://thehackernews.com/2026/02/openclaw-bug-enables-one-click-remote.html)
- [Oasis Security](https://www.oasis.security/blog/openclaw-vulnerability)
- [OpenClaw 安全文档](https://docs.openclaw.ai/gateway/security)
