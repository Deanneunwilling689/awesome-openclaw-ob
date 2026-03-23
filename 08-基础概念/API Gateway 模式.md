---
tags:
  - 架构模式
  - Gateway
  - 消息路由
  - 限流
  - 认证
aliases:
  - API Gateway
  - 网关模式
  - Gateway 模式
---

# API Gateway 模式

## 一句话理解

> API Gateway 是系统的"统一前门"——所有请求先经过它，由它负责认证、路由、限流和协议转换。OpenClaw 的 Gateway（默认端口 18789）就是这一模式的典型实现，是整个 Agent 系统的中枢神经。

## 核心概念

### Gateway 模式的核心职责

| 职责 | 说明 |
|------|------|
| **认证鉴权** | 验证请求者身份，拒绝未授权访问 |
| **请求路由** | 将请求转发到正确的后端服务 |
| **限流** | 控制请求速率，防止过载 |
| **协议转换** | 统一不同来源的消息格式 |
| **状态管理** | 维护会话和连接状态 |

### OpenClaw Gateway 的实现

[[OpenClaw 是什么|OpenClaw]] 的核心是一个 Hub-and-Spoke 架构，Gateway 作为 WebSocket 服务器（`ws://127.0.0.1:18789`）承担所有 API Gateway 职责：

- **消息路由**：WhatsApp、Telegram、Discord 等 13+ Channel Adapter 的消息统一汇聚到 Gateway
- **认证**：QR 码（WhatsApp）、Bot Token（Telegram/Discord）、DM 配对码（未知发送者）
- **会话隔离**：同一用户在 WhatsApp 和 Telegram 上拥有两个独立 Session
- **并发控制**：[[Lane-Based Queuing 并发模型|Lane-Based Queuing]]，单写者规则——每个会话同一时间只能有一个 Agent 运行
- **全局限流**：`maxConcurrent` 默认 10 个并行请求

### 多 Agent 路由

Gateway 支持一个实例托管多个 Agent，每个 Agent 独立工作空间、模型和行为：

- `group:discord:123456` → Claude Sonnet + discord-bot 工作空间
- `dm:telegram:*` → GPT-4o + support-agent 工作空间 + 强制沙箱

## 应用与影响

- **安全关键点**：Gateway 是 OpenClaw 安全模型的核心——CVE-2026-25253 正是通过跨站 WebSocket 劫持窃取 Gateway 认证令牌实现 RCE 的
- **默认绑定风险**：早期版本默认绑定 `0.0.0.0:18789`（公网），导致 40,000+ 实例暴露
- **端口分离设计**：Canvas UI（18793）与 Gateway（18789）分离，实现故障隔离——Canvas 崩溃不影响核心通信
- **WebSocket 心跳**：30 秒心跳检测 + 指数退避重连，保证持久连接稳定性

## 关键洞察

OpenClaw Gateway 的设计印证了一个架构原则：**Gateway 既是最强大的安全层，也是最大的单点故障**。CVE-2026-25253 的攻击链表明，一旦 Gateway 认证被突破，攻击者可以关闭用户确认、逃出沙箱、在宿主机执行任意命令。这就是为什么安全厂商建议 Gateway 必须绑定 localhost、启用 TOFU 策略、并部署 Origin 头验证。

## 双链导航

- [[OpenClaw 是什么]] — Gateway 是 OpenClaw 的核心组件
- [[Agent Execution Loop]] — Gateway 触发的 6 阶段处理流程
- [[Lane-Based Queuing 并发模型]] — Gateway 的并发控制机制
- [[消息路由]] — Gateway 的路由策略详解
- [[安全边界与风险（总览）]] — Gateway 暴露带来的安全风险
- [[多Agent协作架构]] — Gateway 支撑的多 Agent 路由能力
