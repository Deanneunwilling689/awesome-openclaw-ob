---
tags:
  - 案例
  - 多人格
  - 个人助理
  - OpenClaw
aliases:
  - 三个AI人格
  - Morty
  - Pepper Potts
  - David Goggins
---

# 案例：三个 AI 人格深度评测

**人物**：AI Maker Substack 博主
**部署**：Hetzner VPS，创建三个专业化人格

## 三个人格分工

| 人格 | 角色 | 职责 |
|------|------|------|
| **Morty**（Sidekick） | 跑腿助手 | 探索新工具、Netflix 推荐、Spotify 健身歌单 |
| **Pepper Potts**（Chief of Staff） | 幕僚长 | 管理 Newsletter、咨询工作、Notion 数据库、Todoist，每天发送早报 |
| **David Goggins**（Accountability Coach） | 健身教练 | 每晚检查锻炼完成度、存储健身日志、个性化激励 |

## 核心体验变化

> "After setup, I stopped visiting apps directly. Notion, email, and task management became invisible—handled automatically."

这体现了 [[Agent-Flow-Loop 原理]] 的核心价值——Agent 接管了日常应用的交互层，用户只需通过自然语言沟通。三个人格的设计也展示了 System Prompt 如何塑造不同的 Agent 行为模式。

## 技术与架构

三个人格的分工体现了 多Agent协作架构 的"个人版"实践。每个人格通过不同的 Tool Use 机制 访问不同的服务——Pepper Potts 管理 Notion 和 Todoist，Morty 访问 Netflix 和 Spotify，David Goggins 管理健身日志。这种设计暗含了 权限控制机制 的思想——每个人格只拥有执行其职责所需的最小权限。人格背后的 记忆系统 使得 Agent 能够记住用户偏好，实现个性化服务。

## 成本

- VPS：€5-7/月
- API 调用费另计

与 [[案例-MFS Corp 零人类员工 AI 公司]] 的 $50/月成本类似，这些案例都展示了 OpenClaw 部署成本的低廉。模型无关架构允许灵活选择性价比最优的 大语言模型，而 API 定价与成本分析 的数据表明个人用户的月均成本可以控制在极低水平。这也是 可及性突破 的重要组成部分——AI 助手不再是大企业的专利。

## 来源

- [AI Maker Substack - OpenClaw Review Setup Guide](https://aimaker.substack.com/p/openclaw-review-setup-guide)
- [Hacker News Discussion](https://news.ycombinator.com)
- [The Verge - AI Personal Assistants](https://theverge.com)

## 相关笔记

- [[案例-MFS Corp 零人类员工 AI 公司]]
- [[案例-Jesse Genet 家庭教育系统]]
- [[Agent-Flow-Loop 原理]]
