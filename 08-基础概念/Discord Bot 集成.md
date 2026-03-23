---
title: Discord Bot 集成
tags:
  - OpenClaw
  - channel
  - Discord
  - community
aliases:
  - Discord 集成
  - Discord Bot
created: 2026-03-14
updated: 2026-03-14
type: concept
status: evergreen
---

## 一句话解释

Discord Bot 通过 discord.js 库将 AI Agent 植入社区服务器，[[OpenClaw 是什么|OpenClaw]] 在 Discord 上同时扮演社区成员和个人助手的双重角色。

## 费曼式展开

Discord 不是普通的聊天工具，它是一个**有结构的社区空间**——有频道、有权限、有角色。把 AI Agent 放进这个空间，它不只是回答问题，还能管理社区、总结讨论、触发自动化工作流。

**Discord Bot 开发生态（2026）：**
- discord.js 是最主流的 JavaScript Bot 框架
- 支持斜杠命令（`/ask`、`/summarize`、`/help`）
- 支持按频道设置不同的系统提示词，同一个 Bot 在不同频道有不同"人格"
- 2026 年趋势：从简单聊天机器人向**自主 AI Agent** 演进，能推理、记忆、调用工具

**OpenClaw 的 Discord 集成——双重角色：**

**角色一：个人 AI 助手**
- 在 DM（私信）中与你一对一对话
- 执行任务：清理邮箱、管理日历、查询信息
- 与其他频道（WhatsApp、Telegram）共享同一个记忆和上下文

**角色二：社区工具**
- OpenClaw 自身的 Discord 社区就是项目的核心沟通阵地
- Bot 在公开频道中为社区成员提供技术支持
- 自动审核、内容总结、FAQ 问答

**技术实现要点：**
- 通过 **discord.js** 库连接 Discord Gateway
- 支持事件驱动架构——消息、反应、频道事件都可触发 Agent 工作流
- 斜杠命令提供结构化交互入口
- 每个频道适配器运行在独立线程，与其他频道互不干扰

**与其他频道的互补关系：**
- WhatsApp/Telegram 适合**个人 1:1 场景**
- Discord 适合**社区 + 协作场景**
- 三者通过 OpenClaw 的统一消息架构无缝连接，用户在任何平台的对话都有统一上下文

**2026 年 Discord AI Bot 成本参考：**
- 预构建方案（MEE6 等）：$10-30/月
- 无代码平台方案：$30-100+/月
- 自定义开发：$300-3000+ 一次性 + $5-50+/月运维

## 双链

- [[OpenClaw 是什么]]
- [[OpenClaw Discord 社区]]
- [[多频道消息架构]]
