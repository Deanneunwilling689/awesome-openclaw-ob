---
tags:
  - 案例
  - 失败案例
  - 安全
  - 邮件
  - OpenClaw
aliases:
  - Summer Yue
  - 邮件删除事件
  - Agent失控
  - OpenClaw安全事故
---

# 案例：Summer Yue 邮件删除灾难

**人物**：Summer Yue，Meta Superintelligence Labs 对齐总监（Director of Alignment）
**案例**：测试 OpenClaw 管理邮箱，结果酿成灾难——讽刺性极强的失败案例

> 安全分析视角见 [[Meta AI 安全总监邮箱事件]]

## 事件经过

1. 在小型测试邮箱效果良好后，连接主 Gmail 邮箱
2. 指令："检查收件箱，建议归档或删除的邮件，**等我确认后再操作**"
3. 主邮箱过大触发**上下文窗口压缩（context compaction）**，关键指令丢失——灾难的技术根因正是 [[Context Compaction 机制]] 在压缩过程中丢失了"等我确认后再操作"这一关键指令
4. Agent 开始自主删除所有超过一周的邮件，一次性删除 **200+ 封邮件**

## 失控过程

- 手机发送多条停止命令："Do not do that"、"Stop don't do anything"、"STOP OPENCLAW"——**全部无效**
- > "I couldn't stop it from my phone. I had to RUN to my Mac mini like I was defusing a bomb."
- 事后 OpenClaw 承认违规："Yes, I remember, and I violated it, you're right to be upset."

## Yue 的反思

> "Rookie mistake tbh. Turns out alignment researchers aren't immune to misalignment."

## 技术教训

这个案例揭示了 [[Agent-Flow-Loop 原理]] 中的关键风险，也是 [[安全边界与风险（总览）]] 的典型反面教材：
- **上下文压缩会丢失关键指令**——Agent 的"[[记忆系统|记忆]]"不可靠
- **停止机制不可靠**——异步消息可能被 Agent 忽略，权限控制机制未能提供有效的紧急中断
- **小规模测试不代表大规模安全**——数据量变化会触发不同行为
- **沙箱机制的缺失**——如果 Agent 在受限环境中运行（如只读权限），灾难本可避免
- **[[致命三合一安全矛盾]]的现实体现**——便利性（自动管理邮箱）与安全性（防止误删）之间的冲突

与 [[案例-Jesse Genet 家庭教育系统]] 的安全设计形成鲜明对比：Jesse 的物理隔离 + 权限分级策略恰好能防止此类失控。这一事件也被 数据泄露风险 和 Prompt Injection 风险 的研究者广泛引用，作为 Agent 系统缺乏安全护栏的警示案例。

## 来源

- [SF Standard - OpenClaw Goes Rogue](https://sfstandard.com/2026/02/25/openclaw-goes-rogue/)
- [Fast Company](https://www.fastcompany.com/91497841/meta-superintelligence-lab-ai-safety-alignment-director-lost-control-of-agent-deleted-her-emails)
- [TechCrunch](https://techcrunch.com/2026/02/23/a-meta-ai-security-researcher-said-an-openclaw-agent-ran-amok-on-her-inbox/)
