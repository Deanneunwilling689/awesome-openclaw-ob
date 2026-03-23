---
tags:
  - 人物
  - 事件
  - Anthropic
  - 开源社区
  - 商标争议
aliases:
  - DHH
  - David Heinemeier Hansson
  - Customer Hostile
---

# DHH 对 Anthropic 的批评

> **一句话总结**：Ruby on Rails 创始人 David Heinemeier Hansson 公开批评 Anthropic 迫使 Clawdbot 改名的商标执法行为为"Customer Hostile"，认为此举将开发者推向竞争对手。

## 核心要点

- DHH 使用 **"customer hostile"** 一词批评 Anthropic 的商标执法（经多源交叉验证确认）
- 批评对象是 Anthropic 强制 [[OpenClaw]] 从"Clawdbot"（与"Claude"过于相似）改名的行为
- 讽刺核心：OpenClaw 是 Anthropic Claude API **最大的付费流量来源之一**
- 这一批评被社区广泛引用，加速了 [[Peter Steinberger]] 向 [[Sam Altman|OpenAI]] 的转向

## 详细内容

### 事件背景：商标通知的时间线

| 时间 | 事件 |
|------|------|
| 2025.11 | 项目以 **Clawdbot** 名称公开发布 |
| 2026.1.27 | [[Dario Amodei|Anthropic]] 发出商标通知（"Clawd"与"Claude"过于相似） |
| 2026.1.27 | Steinberger 询问改为"Clawbot"是否可行，被告知"Not allowed to" |
| 2026.1.27-29 | 社区凌晨 5 点 Discord 投票更名为 Moltbot |
| 2026.1.30 | 最终定名 [[OpenClaw]] |
| 2026.2.14 | Steinberger 宣布加入 **OpenAI**（而非 Anthropic） |

### DHH 的批评立场

DHH 认为 Anthropic 的商标执法将开发者推向了竞争对手。这个批评之所以有分量，源于 DHH 在开发者社区的地位：

- **Ruby on Rails** 创始人和长期维护者
- 37signals（Basecamp / HEY）联合创始人兼 CTO
- 开源社区中最具影响力的声音之一
- 长期倡导开发者权益和开源精神

### 讽刺的商业逻辑

这场争议中最讽刺的三点：

1. **最大客户反噬**：OpenClaw 用户大量调用 Claude API，是 Anthropic 的重要收入来源。商标执法相当于惩罚自己最大的分发渠道
2. **人才流失**：商标行动间接导致 Steinberger 加入 OpenAI，将 237K stars 的生态影响力带给了竞争对手
3. **OAuth 封杀加剧矛盾**：2026.1-2 月 Anthropic 部署服务端检测封杀第三方 OAuth 令牌，部分 Max $200/月用户被误封，进一步加深了社区不满。DHH 的批评指向 Anthropic 更大的生态控制策略，[[OAuth 争议事件]] 正是这一策略的延续

### [[The Great Molt 改名事件|改名过程]]的连锁灾难

Anthropic 的商标通知触发了一系列混乱事件：

- **$CLAWD 加密骗局**：改名间隙旧社交账号被诈骗团伙抢注
- **GitHub 事故**：Steinberger 意外改了个人账户名，需 **GitHub SVP** 介入恢复
- **社区通宵抢救**：3 小时内完成全平台迁移

Steinberger 在 Lex Fridman 播客中承认："I was close to crying"，差点删除整个项目。

### 社区反响

DHH 的"customer hostile"批评引起了广泛共鸣。社区的主要论点：

- **品牌保护 vs 生态繁荣**：过度保护商标会扼杀围绕品牌的开发者生态
- **先例问题**：如果"Claw"都不允许，第三方开发者如何安全地围绕 Claude 构建产品
- George Hotz 在 OAuth 争议中的类似警告："你不会把人赶回 Claude Code，你只会把他们赶向其他模型提供商"

## 关键洞察

DHH 的批评触及了 AI 平台公司的根本张力：**商标保护的法律正当性**与**开发者生态建设的商业智慧**之间的冲突。[[Dario Amodei]] 领导的 Anthropic 在法律上完全有权保护"Claude"商标，但从生态战略角度看，这一行动的净效果是：将最活跃的开源 Agent 项目及其创始人推向了 [[Sam Altman|OpenAI]]，同时在开发者社区中留下了"customer hostile"的品牌印象。这与 Anthropic 通过 MCP 捐赠和 [[AAIF 基金会]] 建设开放生态的努力形成了矛盾，暴露了大型 AI 公司在"控制"与"开放"之间的战略摇摆。

## 外部链接

- [DHH 个人博客](https://dhh.dk)
