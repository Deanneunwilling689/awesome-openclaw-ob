---
tags:
  - 案例
  - 家庭教育
  - 多Agent
  - 安全设计
  - OpenClaw
aliases:
  - Jesse Genet
  - 家庭教育Agent
  - 五个Agent
---

# 案例：Jesse Genet 家庭教育系统

**人物**：Jesse Genet，四个孩子的家庭教育妈妈
**案例**：一摞 Mac Mini 上运行 5 个 Agent，**从未打开过终端**

## 五个 Agent 分工

| Agent | 角色 | 职责 |
|-------|------|------|
| **Sylvie** | 家庭教育 | 课程书籍照片 → 结构化课程计划，Gemini 生成水彩画教学插图 |
| **Cole** | 编程开发 | 4 天内构建自定义儿童电视 APP，无评论/推荐/兔子洞（Vibe Coding 实例） |
| **Finn** | 财务管理 | 只读银行账单，仅能在私有 Slack 频道通信（权限控制机制实践） |
| **Claire** | 日程安排 | 可使用 iMessage，但无权访问财务数据 |
| 第五个 Agent | 运营 | 整合 Obsidian "第二大脑"（记忆系统实践） |

## 安全设计亮点

这是 [[安全边界与风险（总览）]] 最佳实践的典范：

- **物理隔离**：每个 Agent 独立 Mac Mini，防止跨污染
- **渐进式信任**：像对待新员工一样，先给有限权限，逐步扩展
- **邮箱代理**：Agent 不使用个人邮箱，拥有各自独立邮箱地址
- **教具数字化**：拍摄家中所有教育玩具和物资，创建 AI 驱动的实物库存

## 意义

Jesse 是 [[编程民主化]] 的代表人物——从未打开过终端，却运行着 5 个 Agent 的 [[多Agent协作架构]]，体现了 可及性突破 和 非技术用户真实案例 的核心论点。她的安全设计思路（物理隔离 + 渐进信任）为所有 Agent 部署提供了参考，尤其是与 [[案例-Summer Yue 邮件删除灾难]] 的失控形成鲜明对比。这种人机协作模式下的隔离策略，比依赖Docker 容器化的软件隔离更加彻底。她的案例也证明了 OpenClaw 的 Tool Use 机制 足以支撑非技术用户完成复杂的日常任务。

## 来源

- [ChatPRD Blog - Jesse Genet's 5 OpenClaw Agents](https://www.chatprd.ai/how-i-ai/jesse-genets-5-openclaw-agents-for-homeschooling-app-building-and-physical-inventories)
- [Lenny's Newsletter](https://www.lennysnewsletter.com/p/5-openclaw-agents-run-my-home-finances)
- [Fast Company - AI in Homeschooling](https://fastcompany.com)
- [Hacker News Discussion](https://news.ycombinator.com)
