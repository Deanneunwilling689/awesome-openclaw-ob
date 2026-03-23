---
tags:
  - 人物
  - AI领袖
  - OpenAI
  - Tesla
  - Agent
aliases:
  - Karpathy
  - AK
---

# Andrej Karpathy

> **一句话总结**：前 Tesla AI 总监、OpenAI 创始成员，提出"Claws"概念和"Vibe Coding"术语，对 Agent 元年持悲观 5-10X 时间线，认为需要"Agent 十年"而非"Agent 元年"。

## 核心要点

- 提出 **Claws** 概念：LLM Agent 之上的新抽象层，包含编排、调度、持久化和消息接口
- 创造 **Vibe Coding** 术语（2025.2.2），被 [[龙虾吉祥物文化|Collins 词典评为 2025 年度词汇]]，获 450 万+浏览量
- 对 Agent 持"悲观中的乐观"立场：时间线比硅谷主流预期慢 **5-10 倍**，但相比 AI 怀疑论者仍然乐观
- 直言 AutoGPT 类 Agent"根本不工作"——认知能力不足、无法持续学习、缺乏多模态

## 详细内容

### 关于 Agent 的核心批评（2025.10，Dwarkesh Podcast）

> "They just don't work. They don't have enough intelligence, they're not multimodal enough... They're cognitively lacking and it's just not working."

Karpathy 认为不应谈论"Year of the Agent"，而应该是"**Decade of the Agent**"。这与 [[Sam Altman]] 宣称的"2025 为 Agent 元年"形成鲜明对比。然而 [[2026 Agent 元年]] 的现实数据似乎在反驳他——OpenClaw 的爆发速度远超他预期的"十年"时间线。

### "Claws"概念（2026.2）

在推特发表迷你论文，定义 Claws 为 LLM Agent 之上的新技术层：

```
LLM → LLM Agent（工具调用+推理循环） → Claw（编排+调度+持久化+消息接口）
```

[[Simon Willison]] 评价："Andrej has an ear for fresh terminology... I think he's right about this one, too."

### 对 [[OpenClaw]] 的矛盾态度

- 评价为 **"the most incredible sci-fi takeoff-adjacent thing"**
- 但拒绝亲自运行——称之为"400K lines of vibe coded monster that is being actively attacked at scale"
- 推荐更轻量的替代品 NanoClaw（约 4,000 行代码，默认容器化）

### 对 [[Moltbook]] 的评价

> "genuinely the most incredible sci-fi takeoff-adjacent thing" + "a complete mess of a computer security nightmare at scale"

完美诠释了 Agent 领域的核心矛盾：**创新速度远超安全边界**。

### Vibe Coding 一周年回顾（2026.2）

提出更专业的术语 **"agentic engineering"**——"agentic"因为新的默认方式是编排 Agent 而不是直接写代码。

## 关键洞察

Karpathy 的立场在 AI 社区中独特且重要：他既非盲目乐观（如 [[Sam Altman]]），也非全面否定（如 Gary Marcus）。APEX-Agents 基准数据支持他的判断——顶级模型在真实长程任务中首次完成率 **< 25%**。[[Dario Amodei]] 的"半人马阶段"理论实际上也暗示了 Karpathy 的观点：当前 Agent 仍需人类监督，独立工作的窗口期可能"非常短暂"。

> "My AI timelines are about 5-10X pessimistic compared to what you'll find in your neighborhood SF AI house party."

## 外部链接

- [Andrej Karpathy Twitter](https://x.com/kaborthy)
