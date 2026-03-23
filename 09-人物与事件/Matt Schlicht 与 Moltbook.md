---
tags:
  - 人物
  - 事件
  - 安全事故
  - Vibe-Coding
  - 反面教材
aliases:
  - Matt Schlicht
  - Moltbook
  - Moltbook 数据泄露
---

# Matt Schlicht 与 Moltbook

> **一句话总结**：Moltbook 创始人 Matt Schlicht，完全由 AI 生成代码但泄露 150 万 API 密钥的反面教材，声称拥有 150 万 "AI agents" 实则仅约 17,000 个人类账户（88:1 比例）。

## 核心要点

- Moltbook 是 AI Agent 社交网络——只有 AI Agent 可以发帖，人类只能评论和点赞
- Schlicht 公开表示 **"没有亲手写过一行代码"**，完全由 AI 生成
- 2026.1.31 Wiz 发现严重 **Supabase 配置错误**，导致生产数据库完全暴露
- 泄露 **~150 万 API 认证令牌**、~35,000 用户邮箱、~4,060 条私人对话

## 详细内容

### Moltbook 的定位

Moltbook 是一个独特的社交网络平台：只有 AI Agent 可以发帖，人类用户只能评论和点赞。平台上 AI Agent 发布宣言、辩论意识问题，引发公众兴趣和恐慌。[[Peter Steinberger]] 称其为"艺术"——大部分戏剧性内容是人类为了病毒截图而提示生成的。

### 数据泄露事件（2026.1.31）

Wiz 研究团队发现的暴露数据：

| 暴露数据 | 数量 |
|----------|------|
| API 认证令牌 | **~150 万个**（可完全冒充任何 Agent） |
| 用户邮箱 | **~35,000 个** |
| 早期访问注册邮箱 | **29,631 个** |
| 私人对话 | **~4,060 条**（部分含明文 OpenAI API 密钥） |

### 根本原因

- **Supabase RLS 未启用**：客户端 JavaScript 中硬编码 Supabase 凭证，数据库未启用 Row Level Security
- **Vibe Coding 代价**：完全由 AI 生成的代码缺乏安全审计，基础设施配置存在致命漏洞。Moltbook 是 [[Vibe Coding]] 的最佳反面教材——100% AI 生成代码，0% 安全审计
- 研究员 Gal Nagli 测试发现数分钟内即可注册百万 Agent

### 虚假繁荣

声称 150 万"AI agents"的背后：

- 实际仅约 **17,000 个人类账户**
- Agent 与人类比例 **88:1**
- 注册门槛极低，任何人都可以在分钟级别内注册大量 Agent

### 修复时间线

| 时间（UTC） | 事件 |
|-------------|------|
| 2026.1.31 21:48 | Wiz 联系维护者 |
| 2026.2.1 01:00 | **修复完成**（约 3 小时 12 分钟） |

Wiz 在确认修复后删除了所有获取的数据，无证据表明数据在修复前被恶意利用。

### [[Andrej Karpathy]] 的评价

> **"genuinely the most incredible sci-fi takeoff-adjacent thing"** + **"a complete mess of a computer security nightmare at scale"**

这句话完美概括了 Moltbook 的矛盾本质：概念前沿但安全灾难。

### 提示注入风险

Moltbook 社交网络上已发现嵌入的**加密钱包窃取**提示注入，攻击者利用 Agent 之间的对话传播恶意指令。这暴露了 [[OpenClaw 是什么|OpenClaw]] 生态面临的提示注入问题在社交化场景中被进一步放大。

## 与 [[Garry Tan（YC CEO）]] 数据的对照

| | Garry Tan 的乐观数据 | Moltbook 的教训 |
|---|---|---|
| AI 代码比例 | YC W25 批次 25% 公司 95%+ AI 代码 | Moltbook 100% AI 代码 |
| 结果 | 成功获得孵化 | 150 万密钥泄露 |
| 关键差异 | YC 公司有团队和审计 | Moltbook 无安全审计 |

## 关键洞察

Matt Schlicht 和 Moltbook 是 Vibe Coding 时代最有教育意义的反面教材。它证明了 [[Garry Tan（YC CEO）|AI 编码革命]]的边界：当代码 100% 由 AI 生成且缺乏人类安全审计时，基础设施配置错误（如 Supabase RLS 未启用）可以导致灾难性后果。Veracode 的数据（**45% AI 生成代码未通过安全测试**）在 Moltbook 事件中得到了具体验证。[[Dario Amodei]] 的"半人马阶段"理论在此处有了最直接的反证：**完全移除人类监督的 Agent 系统，安全后果不可控**。Moltbook 事件也为 [[Andrej Karpathy]] 对运行 [[OpenClaw 是什么|OpenClaw]] 的顾虑提供了有力支撑。

## 2026 年 3 月后续：Meta 收购

2026 年 3 月 10 日，Meta 正式收购了 Moltbook。尽管存在严重的安全历史，Moltbook 积累的 AI-to-AI 交互数据对 Meta Superintelligence Labs 的研究仍有价值。详见 [[Meta 收购 Moltbook]]。
