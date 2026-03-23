---
tags:
  - Claude-Code
  - 架构
  - Agentic-Coding
aliases:
  - Claude Code
  - Claude Code 架构
---

# Claude Code 的技术架构

Claude Code 是 Anthropic 开发的 [[Agentic Coding]] 工具，基于 Claude 模型系列运行在终端/IDE 环境中，专注于代码编辑、终端操作和 Git 工作流。

## 与 OpenClaw 的架构对比

Claude Code 同样采用 Agent 执行循环，但设计哲学与 [[OpenClaw 是什么|OpenClaw]] 有本质区别：

| 特性 | Claude Code | OpenClaw |
|------|------------|----------|
| 运行模式 | 会话制，用完即关 | 24/7 持续运行 |
| 界面 | 终端 / IDE | 聊天应用（WhatsApp 等） |
| 记忆 | 会话内上下文 + Compaction | 跨会话持久记忆 + 向量检索 |
| 工具范围 | 代码编辑、终端、Git | 文件、浏览器、邮件、日历、智能家居 |
| 沙箱 | 内置沙箱 | Docker 容器（可选） |
| 自我修正 | 强（SWE-bench 80.8%） | 有限 |

## 核心特点

- **会话制运行**：启动后在当前工作目录中执行任务，完成后退出
- **内置沙箱**：相比 OpenClaw 的可选 Docker 沙箱，Claude Code 有内置的安全沙箱
- **强自我修正**：在 SWE-bench 上达到 80.8% 的得分，显示出强大的代码修正能力
- **[[Tool Use 机制]]**：专注于代码相关工具——文件读写、终端命令、Git 操作
- **系统提示设计**：精心设计的系统提示词控制 Agent 行为边界

## 上下文管理

Claude Code 使用 Compaction 机制管理上下文，这与 OpenClaw 的多层记忆系统不同。Claude Code 的上下文主要在单次会话内有效，不像 OpenClaw 那样拥有跨会话的持久记忆。

## 相关笔记

- [[Agentic Coding]]
- [[Agent Execution Loop]]
- [[Tool Use 机制]]
- [[OpenClaw 是什么]]

## 参考

- [Anthropic Claude Code 官方文档](https://docs.anthropic.com/en/docs/claude-code)
- [Anthropic 官网](https://anthropic.com)
