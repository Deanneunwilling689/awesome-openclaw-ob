---
tags:
  - 人物
  - AI领袖
  - Anthropic
  - Claude
  - Agent安全
aliases:
  - Amodei
  - Anthropic CEO
---

# Dario Amodei

> **一句话总结**：Anthropic CEO，提出"半人马阶段"理论（人+AI 组合当前最强），Claude 背后的决策者，在 AI 安全与商业化之间走钢丝。

## 核心要点

- 提出 **"半人马阶段"（centaur phase）** 理论：人 + AI Agent 的组合是当前最强大的单元
- 领导 Anthropic 达到 $380 亿估值（Series G），[[Claude Code]] 年化营收 **$25 亿**（2026.2）
- 推动 [[Constitutional AI]] 安全框架，但因商标执法引发社区争议
- 将 MCP（Model Context Protocol）捐赠给 [[AAIF 基金会]]，月 SDK 下载 9700 万+

## 详细内容

### 半人马阶段理论（2026.2.23，Axios 报道）

> "人类检查 AI 的走法可以击败独立的 AI 或人类，但机器后来完全超越了这种安排。"

Amodei 以国际象棋为类比：15-20 年前，人机组合（"半人马"）可以击败纯 AI 或纯人类。他警告这个窗口期可能"**非常短暂**"。这与 [[Andrej Karpathy]] 的"Agent 十年"论形成有趣的对比：

- Karpathy：Agent 需要十年才能独立工作
- Amodei：人机协作阶段存在，但窗口期正在关闭

### Claude 生态的商业数据

| 指标 | 数值 |
|------|------|
| Claude Code 年化营收 | **$25 亿**（2026.2，翻倍增长）—— [[Claude Code 营收分析]] 详述了这一增长，半人马理论的最佳证明就是 Claude Code 营收翻倍：人+AI 确实更强 |
| Anthropic 估值 | **$380 亿**（Series G） |
| SWE-bench Verified（Opus 4.6） | **80.8%**（最高） |
| VS Code 日安装量 | 2900 万 |
| 企业订阅占比 | 超过 50% |

### 与 OpenClaw 的微妙关系

Amodei 领导的 Anthropic 对 [[OpenClaw]] 的商标执法（"Clawd"与"Claude"过于相似）产生了连锁反应：

1. 发出商标通知迫使改名 → 引发 [[The Great Molt 改名事件]]
2. [[DHH 对 Anthropic 的批评|DHH 公开批评]]为"customer hostile"
3. 创始人 Steinberger 最终加入了 **OpenAI** 而非 Anthropic
4. 讽刺之处：OpenClaw 是 Claude API 最大的付费流量来源之一

### OAuth 封杀争议（2026.1-2）

Anthropic 部署服务端检测，封杀所有第三方工具使用 Claude 订阅 OAuth 令牌。部分 Max $200/月用户因误触滥用过滤器被封号。George Hotz 警告："你不会把人赶回 Claude Code，你只会把他们赶向其他模型提供商。"

### MCP 捐赠与 AAIF

Mike Krieger（Anthropic CPO）代表公司将 MCP 捐赠给 Linux Foundation 旗下的 [[AAIF 基金会]]：

> "Donating MCP to the Linux Foundation ensures it stays open, neutral, and community-driven as it becomes critical infrastructure for AI."

MCP 已有 **9700 万+月 SDK 下载**和 **10,000+ 活跃服务器**，成为 Agent 工具连接的事实标准。

## 关键洞察

Amodei 的战略困境在于：他既要推动 Claude 的商业化（$25 亿营收），又要维护 AI 安全的品牌形象（[[Constitutional AI]]）。商标执法事件暴露了这种张力——保护品牌的合理行为，却被社区解读为对开源生态的敌意，最终将 [[Peter Steinberger]] 和整个 OpenClaw 生态推向了竞争对手 [[Sam Altman|OpenAI]]。半人马阶段理论本身是深刻的，但它也隐含了一个不安的预测：人类的"必要性"窗口正在关闭。

## 外部链接

- [Anthropic 公司官网](https://anthropic.com/company)
