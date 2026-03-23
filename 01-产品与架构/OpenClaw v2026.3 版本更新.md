---
tags:
  - OpenClaw
  - 版本更新
  - 2026年3月
  - changelog
aliases:
  - v2026.3
  - OpenClaw v2026.3
  - 3月版本更新
  - v2026.3.12
  - v2026.3.13
  - v2026.3.22
---

# OpenClaw v2026.3 版本更新

## 一句话理解

> 2026 年 3 月是 OpenClaw 架构大变革月——Dashboard 全面模块化、模型提供商迁移到 [[Provider-Plugin 架构]]、[[可插拔沙箱后端]] 引入 OpenShell、插件 SDK 路径 Breaking Change，标志着框架从"功能堆叠"进入"系统级模块化"阶段。

## 版本总览

| 版本 | 发布日期 | 性质 | 核心主题 |
|------|----------|------|----------|
| v2026.3.12 | 3月13日 | 正式版 | Dashboard 刷新 + Provider-Plugin 架构 |
| v2026.3.13-1 | 3月14日 | 热修复 | 性能优化 + 平台适配修复 |
| v2026.3.22-beta.1 | 3月23日 | Beta | ClawHub 原生安装 + 可插拔沙箱 + Breaking Changes |

---

## v2026.3.12（3月13日）— Dashboard 刷新与插件化架构

### Dashboard UI 全面刷新

- 模块化视图拆分为五大独立模块：overview、chat、config、agent、session
- 新增**命令面板（Command Palette）**，支持键盘快捷搜索与导航
- 移动端优化底部标签栏，改善小屏体验

详见 [[Dashboard 控制面板]]。

### 模型提供商插件化

- **OpenAI GPT-5.4 fast mode** 支持
- **Anthropic Claude fast mode** 集成
- Ollama、vLLM、SGLang 迁移到 [[Provider-Plugin 架构]]（模块化提供商插件）
- MiniMax 和 xAI 模型目录对齐

这是 [[模型无关架构]] 的重大工程落地——从"配置驱动切换"升级为"插件驱动扩展"。

### 新增捆绑插件

- **Chutes**：模型推理加速
- **Exa**：网页搜索能力
- **Tavily**：AI 原生搜索引擎集成
- **Firecrawl**：网页爬取与数据提取

这些插件通过 [[Plugin 扩展系统]] 的 `openclaw.extensions` 机制注册，开箱即用。

### 部署

- 新增 **Kubernetes 部署文档**，覆盖 Helm Chart 和高可用配置

---

## v2026.3.13-1（3月14日）— 热修复与性能优化

此版本修复损坏的 v2026.3.13 标签，并带来多项稳定性改进：

### 性能

- **Dashboard 聊天历史重加载性能优化**：大量历史会话场景下加载速度显著提升
- **会话状态跨重置保持**：重启 Gateway 后会话状态不再丢失，与 [[会话状态管理]] 的 JSONL 持久化机制配合

### 平台修复

- **Discord 网关元数据处理改进**：修复特定消息类型的元数据解析问题
- **Ollama 推理可见性修复**：本地模型推理过程现在可在 Dashboard 实时查看
- **Android 聊天设置重新设计**：移动端配置界面优化
- **macOS exec approval 集成**：macOS 平台执行审批流程原生集成，增强 [[自主执行与人机协作|人机协作]] 安全性

---

## v2026.3.22-beta.1（3月23日）— 最新 Beta：沙箱与 SDK 重构

这是 3 月最重要的版本，引入多项架构级变更和 Breaking Changes。

### ClawHub 原生安装

- ClawHub 安装流程整合进核心，无需额外配置即可从 [[ClawHub 官方技能注册表]] 安装 Skills

### 可插拔沙箱后端

- **OpenShell 后端**：支持 mirror 和 remote 两种工作区模式
- **核心 SSH 后端**：用于远程执行场景

详见 [[可插拔沙箱后端]]。

### 浏览器自动化增强

- 批量操作支持
- 选择器定位优化
- **Chrome DevTools MCP** 集成，通过 [[Chrome DevTools Protocol]] 实现更精细的浏览器控制

### 新增提供商与平台

- **Anthropic Vertex AI 提供商**支持，通过 [[Provider-Plugin 架构]] 接入 Google Cloud 上的 Claude
- **Matrix 插件完全重写**：基于 `matrix-js-sdk`，替代旧的自定义实现

### Breaking Changes

> **插件 SDK 路径迁移**：从 `openclaw/extension-api` 迁移到 `openclaw/plugin-sdk/*` 子路径。所有第三方插件需要更新 import 路径。

> **环境变量统一**：移除所有旧版 `CLAWDBOT_*` 和 `MOLTBOT_*` 环境变量，统一为 `OPENCLAW_*`。这是 [[OpenClaw 的起源与发展历程|改名事件]] 的最终技术清理。

> **移除旧版 Chrome 扩展中继路径**。

> **Discord 原生命令部署**：从旧方案切换为 Carbon reconcile。

## 应用与影响

- **模块化转型完成**：Dashboard 模块化 + Provider 插件化 + 沙箱可插拔，三条线同时推进，OpenClaw 正在从"单体框架"变为"可组装平台"
- **历史包袱清理**：`CLAWDBOT_*`/`MOLTBOT_*` 环境变量和旧 Chrome 中继路径的移除，说明项目有决心切断向后兼容包袱
- **安全改进持续**：macOS exec approval 和可插拔沙箱后端表明安全仍是优先事项

## 关键洞察

v2026.3 系列标志着 OpenClaw 的"第二次架构跃迁"——第一次（v2.1）是安全补课，这一次是工程成熟度提升。Provider-Plugin 架构让模型接入从"PR 合并"变成"npm install"，可插拔沙箱让执行环境从"硬编码"变成"可替换"，Dashboard 模块化让前端从"整块页面"变成"视图组件"。这些变化的共同方向是：**让 OpenClaw 的每一层都可以被独立替换和扩展**。

但 Beta 版中的 Breaking Changes 也是一把双刃剑——对于 ClawHub 上 3,286 个 Skills 和社区 Plugin 生态来说，SDK 路径迁移和环境变量清理意味着不小的迁移成本。

## 双链导航

- [[OpenClaw 是什么]] — 框架总览
- [[OpenClaw v2.1 版本更新]] — 上一个重大版本
- [[Dashboard 控制面板]] — v2026.3.12 引入的 Dashboard 模块化
- [[Provider-Plugin 架构]] — 模型提供商插件化架构
- [[可插拔沙箱后端]] — OpenShell 沙箱后端
- [[Plugin 扩展系统]] — 插件加载与扩展机制
- [[模型无关架构]] — Provider-Plugin 是模型无关的工程落地
- [[会话状态管理]] — 会话状态跨重置保持的改进
- [[自主执行与人机协作]] — macOS exec approval 的安全理念
- [[OpenClaw 的起源与发展历程]] — 环境变量清理与改名事件的关联
- [[Chrome DevTools Protocol]] — 浏览器自动化的底层协议

## 参考

- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
- [OpenClaw Releases](https://github.com/anthropics/openclawx/releases)
