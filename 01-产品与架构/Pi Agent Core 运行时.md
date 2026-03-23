---
tags:
  - 架构
  - 运行时
  - pi-agent-core
  - message-pipeline
aliases:
  - Pi Agent Core
  - Agent 运行时引擎
  - Message Pipeline
  - Mario Zechner
---

# Pi Agent Core 运行时

## 一句话总结

Pi Agent Core 是 OpenClaw 的底层 Agent 运行时引擎，由 libGDX 游戏引擎作者 Mario Zechner 开发——它定义了消息从原始输入到 LLM 调用的完整管道流程，以及 steer/followUp 两种 Agent 流控制 API。

## 核心机制：Message Pipeline

Agent 的消息处理遵循严格的三阶段管道：

```
AgentMessage[] → transformContext() → convertToLlm() → LLM Provider
```

### 阶段一：AgentMessage[]

原始消息数组，包含用户输入、系统提示（IDENTITY.md、SOUL.md 等）、工具调用结果、[[记忆系统|记忆]]搜索结果和 Skill 定义。

### 阶段二：transformContext()

上下文变换——这是管道中最复杂的步骤：
- **注入记忆**：将[[向量嵌入与混合搜索|混合搜索]]找到的相关历史注入上下文
- **裁剪历史**：通过 Pruning 临时裁剪，确保不超模型窗口
- **应用 [[Context Compaction 机制|Compaction]]**：当上下文接近上限时触发压缩
- **Skill 选择性注入**：只注入当前任务相关的 Skill，避免 Token 膨胀

### 阶段三：convertToLlm()

将统一的内部格式转换为特定 LLM Provider 的协议：
- **Anthropic**：Tool Use 格式，原生流式，200K 上下文
- **OpenAI**：Function Calling 格式，delta 流式，严格 RPM/TPM 限制
- **Ollama**：本地模型适配，无需 API Key

同一条消息经过 convertToLlm() 后可以发往任何 Provider——这是[[模型无关架构]]的关键实现。

## 流控制 API：steer 与 followUp

Pi Agent Core 提供两种控制 Agent 执行流的方式，详见[[Steering 与 Follow-Up 控制]]：

| API | 行为 | 控制模式 |
|-----|------|----------|
| `steer()` | 中断当前执行，在 tool boundary 插入新指令 | 抢占式 |
| `followUp()` | 排队等待当前循环完成后执行 | 协作式 |

这两个 API 是[[Lane-Based Queuing 并发模型]]中 steer/followup 队列模式的底层实现。

## Mario Zechner 与 Gateway 的关系

Mario Zechner 是 **libGDX** 游戏引擎的作者。从游戏引擎到 Agent 运行时并非巧合：两者都需要处理**高吞吐量的事件循环、状态管理和实时响应**。

Gateway 负责"谁的消息、发给谁"（调度层），Pi Agent Core 负责"拿到消息后怎么处理"（执行层）。Gateway 调用 Pi Agent Core 执行 Agent 循环，后者管理 Message Pipeline、流控制和工具执行环境。

## 关键洞察

Pi Agent Core 的 Message Pipeline 设计揭示了一个重要的工程原则：**将 LLM 的不确定性封装在确定性的管道中**。transformContext() 和 convertToLlm() 都是纯粹的转换函数——输入确定，输出确定。不确定性只存在于管道的末端（LLM 推理）。这种设计让调试、测试和监控都变得可行——你可以在管道的任何阶段截取中间状态进行审计。

## 相关笔记

- [[Agent-Flow-Loop 原理]] -- Pi Agent Core 是 6 阶段执行循环的引擎
- [[Steering 与 Follow-Up 控制]] -- steer/followUp API 的详细行为
- [[Context Compaction 机制]] -- transformContext() 中触发的压缩机制
- [[TypeBox Schema 工具定义]] -- convertToLlm() 将 Schema 转为 Provider 格式
- [[模型无关架构]] -- convertToLlm() 实现多 Provider 适配
- [[Lane-Based Queuing 并发模型]] -- 流控制 API 与队列模式的映射
- [[上下文管理机制]] -- transformContext() 的上下文变换逻辑

## 参考

- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
- [libGDX 游戏引擎](https://libgdx.com)
