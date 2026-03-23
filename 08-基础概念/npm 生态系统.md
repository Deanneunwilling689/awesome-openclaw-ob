---
title: npm 生态系统
aliases: [npm, Node Package Manager, npm registry]
tags: [概念, 基础设施, 包管理]
created: 2026-03-14
updated: 2026-03-14
type: atomic-note
---

# npm 生态系统

## 一句话解释

npm 就像一个巨型乐高积木仓库——开发者把自己造的"积木"（代码包）放进去，其他人用一行命令就能拿来拼装自己的项目。

## 它到底是什么

npm（Node Package Manager）最初是 Node.js 的包管理器，现在已经成为世界上最大的软件注册表。它做两件事：
1. **注册表**（registry）：一个在线仓库，存放超过200万个开源包
2. **CLI工具**：一个命令行程序，用 `npm install xxx` 就能把包下载到你的项目里

80%以上的npm包至少依赖另一个包——这种高度互联的生态系统既是它的力量来源，也是安全隐患的温床。

## OpenClaw 的 npm 分发

[[OpenClaw 是什么|OpenClaw]] 通过npm分发，包名就叫 `openclaw`：

```bash
npm install -g openclaw@latest
```

要求 Node.js >= 22。这个选择意味着全球数百万JS/TS开发者可以用最熟悉的方式，一行命令安装一个完整的 AI Agent 框架。

关于下载量数据，参见 [[OpenClaw npm 下载数据]]。

## npm 正在成为AI的通用分发平台

2026年一个显著趋势：npm不再只是"JavaScript的包管理器"，而是演变为**AI工具的通用分发渠道**：

- **Anthropic Claude Code** — 通过npm分发
- **Google Gemini CLI** — 通过npm分发
- **[[MCP 协议|MCP SDK]]** — 通过npm分发，已催生6,700+依赖项目

这背后的逻辑是：npm拥有最成熟的版本管理、依赖解析、全球CDN基础设施，而AI工具的主力开发语言正好是 [[TypeScript]]。

## Skills 如何通过 npm 分发

OpenClaw的 [[Skills 市场]] 本质上是npm注册表模式的延伸：

- **ClawHub**：~3,200个Skills，1.5M+下载量
- **Skills.sh**（Vercel出品）：83,627个Skills，8M+总安装量，支持18种不同Agent
- **SkillsMP**：最大目录，89K工具类Skills

Agent可以在运行时自动从注册表搜索和拉取新Skills——就像一个能自己去商店买工具的工人。

## 安全隐患

npm生态的"高度互联"特性在AI时代被放大：

- 2026年1月的 **ClawHavoc** 事件中，1,184个恶意Skills在几天内涌入ClawHub
- **SANDWORM_MODE** 蠕虫攻击了npm供应链，19个伪装成常用工具的恶意包窃取API密钥
- Snyk审计发现13.4%的Skills存在严重安全问题

当一个 AI Agent 能自动安装和执行npm包时，[[恶意 Skills 供应链攻击|供应链攻击]]的影响从"代码受损"升级为"Agent被接管"。

## 外部链接

- [npm 官方网站](https://npmjs.com)

## 双链

- [[OpenClaw 是什么]]
- [[Skills 市场]]
