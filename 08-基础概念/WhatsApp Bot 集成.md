---
title: WhatsApp Bot 集成
tags:
  - OpenClaw
  - channel
  - WhatsApp
  - messaging
aliases:
  - WhatsApp 集成
  - WhatsApp Bot
created: 2026-03-14
updated: 2026-03-14
type: concept
status: evergreen
---

## 一句话解释

WhatsApp Business API 让企业能在全球最大的即时通讯平台上部署 AI Agent——[[OpenClaw 是什么|OpenClaw]] 通过 Baileys 库接入这个拥有 20 亿用户的入口。

## 费曼式展开

想象你开了一家全球连锁店，WhatsApp 就是那条每个人都在走的商业街。你不需要让顾客下载新 App，他们打开 WhatsApp 就能和你的 AI 店员对话。

**WhatsApp Business API 的运作原理：**
1. 用户发送消息到你的商业号码
2. WhatsApp Cloud API 通过 **[[Webhook 技术|Webhook]]** 将消息推送到你的服务器
3. 你的服务器处理消息、调用 AI，生成回复
4. 通过 API 将回复发回给用户

**2026 年的关键变化：**
- Meta 禁止了通用 AI 聊天机器人（OpenAI、Perplexity 等已下线其 WhatsApp bot），但**允许企业用 AI 服务客户**
- Cloud API 成为唯一标准，支持每秒 500 条消息
- 计费模式改为按模板消息送达计费，不再按 24 小时会话收费

**为什么 WhatsApp 是 OpenClaw 的杀手级入口：**
- 覆盖 20 亿用户，无需用户安装任何新应用
- 用户在熟悉的环境中就能指挥 AI Agent 清理邮箱、管理日历、发送邮件
- 端到端加密保障隐私

**OpenClaw 的技术实现：**
- 通过 **Baileys** 库（非官方 WhatsApp Web API）实现连接，使用 TypeScript 开发
- 消息格式支持文本、图片、文件、语音等
- 每个频道适配器运行在独立轻量线程中，不影响其他频道性能
- [[Webhook 技术|Webhook]] 接收入站消息 → [[消息路由|路由]]到 Agent 实例 → 回复通过 API 发出

**消息格式简化示意：**
```
入站 Webhook payload:
{
  "from": "5511999999999",
  "type": "text",
  "body": "帮我查一下明天的日程"
}
```

## 局限性

Meta 对 AI Bot 的政策收紧意味着 OpenClaw 的 WhatsApp 集成必须定位为"具体业务任务"而非通用对话。Baileys 作为非官方库存在被 Meta 封锁的风险。与 [[Telegram Bot API]] 相比，WhatsApp 的限制更多。

## 双链

- [[多频道消息架构]]
