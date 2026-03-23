---
tags:
  - 事件
  - OAuth
  - Anthropic
  - 安全
aliases:
  - OAuth 封杀
  - 令牌套利事件
---

# OAuth 争议事件

> 2026 年 1-2 月

## 背景

2026 年 1 月 9 日，Anthropic 部署服务端检测，封杀所有第三方工具使用 Claude 订阅 OAuth 令牌。

部分用户用 Pro/Max 订阅的 OAuth 令牌接入 OpenCode、Clawdbot 等第三方工具，绕过 API 按量计费（"令牌套利"）。

## 封杀手段

- 令牌作用域绑定
- 遥测验证
- 滥用检测
- 非官方客户端直接报错

## 影响

- OpenCode（56,000+ GitHub Stars）等工具一夜失效
- 部分 Max $200/月用户因误触滥用过滤器被封号
- 这直接影响了 OpenClaw 等依赖 Claude 模型的 Agentic Coding 工具

## 后续发展

- Anthropic 承认误封并回滚部分封禁
- OpenAI Codex 趁机明确支持 ChatGPT 订阅登录，反映了 OpenAI 的竞争策略
- OpenCode 数小时内接入 ChatGPT Plus，体现了 [[模型无关架构]] 的重要性

## 关键声音

> **George Hotz 警告**："你不会把人赶回 Claude Code，你只会把他们赶向其他模型提供商"

## 官方立场

订阅 OAuth 令牌仅限官方 Claude Code 使用，第三方接入需走 API 按量计费。这一事件也引发了开源AI运动社区对平台锁定的广泛讨论。

## 外部链接

- [Claude Code 官方文档](https://docs.anthropic.com/en/docs/claude-code)

## 相关

- [[Claude Code 分析]]
- [[竞品成本对比]]
- [[模型无关架构]]
- [[Anthropic 公司分析]]
