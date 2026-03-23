---
tags:
  - 架构
  - 工具定义
  - TypeBox
  - JSON-Schema
  - 类型安全
aliases:
  - TypeBox Schema
  - 工具 Schema
  - Tool Definition
  - JSON Schema 工具定义
---

# TypeBox Schema 工具定义

## 一句话总结

TypeBox 让 OpenClaw 的工具定义一份代码同时产出 TypeScript 编译期类型和 JSON Schema 运行时验证——LLM 生成的工具调用参数在到达业务逻辑之前必须通过 Schema 校验，不合法的调用被直接拒绝。

## 核心机制：一份定义，双重保障

传统做法需要分别维护 TypeScript 类型定义和 JSON Schema 验证规则，两者容易不同步。TypeBox 用一套 DSL 同时解决两个问题：

```typescript
// 工具参数通过 TypeBox 定义 JSON Schema
const params = Type.Object({
  query: Type.String({ description: "搜索查询" }),
  limit: Type.Optional(Type.Number({ default: 10 }))
});
// 运行时自动验证输入，拒绝不合法的工具调用
```

这段代码做了三件事：
1. **编译期**：TypeScript 自动推导出 `{ query: string; limit?: number }` 类型
2. **运行时**：生成标准 JSON Schema，用于验证 LLM 返回的工具调用参数
3. **文档化**：`description` 字段直接作为 LLM 的工具参数说明

## 在 Agent 执行循环中的位置

```
工具定义注册 → JSON Schema 自动生成 → 注入系统提示（Phase 3）
                                           ↓
                            LLM 返回工具调用请求（Phase 4）
                                           ↓
                         TypeBox 运行时验证参数 → 通过/拒绝（Phase 5）
                                           ↓
                              执行工具逻辑 → 结果回传给 LLM
```

在[[Agent-Flow-Loop 原理]]的 Phase 3（Context Assembly）中，工具定义被自动序列化为 JSON Schema 注入到系统提示。在 Phase 5（Tool Execution Loop）中，LLM 返回的每个工具调用都经过 TypeBox 验证才被执行。

## 跨 Provider 适配与类型安全

不同 LLM Provider 对工具调用有不同协议：Anthropic 用 Tool Use 格式（input_schema），OpenAI 用 Function Calling（parameters 字段），Ollama 适配本地模型。[[Pi Agent Core 运行时]]的 `convertToLlm()` 将同一份 TypeBox Schema 转换为各 Provider 原生格式。

LLM 生成的参数不可信——TypeBox 运行时验证充当**防火墙**：类型不匹配则拒绝执行、缺少必填字段则拒绝让 LLM 重试、多余字段静默忽略。这在[[自我修改软件机制]]场景下尤为关键——Agent 动态添加新工具时 TypeBox 确保参数定义始终类型安全。

## 关键洞察

TypeBox 的选择反映了 OpenClaw 的工程价值观：**在 LLM 的不确定性和系统的确定性之间建立可靠边界**。LLM 是概率性的，它可能生成任何格式的参数；但工具执行是确定性的，它需要精确的输入。TypeBox 就是这个边界上的守门人——让 Agent 在灵活和可靠之间取得平衡。

## 相关笔记

- [[Tool Use 机制]] -- TypeBox 是工具调用的参数验证层
- [[Pi Agent Core 运行时]] -- convertToLlm() 将 Schema 转为 Provider 格式
- [[Agent-Flow-Loop 原理]] -- Phase 3 注入工具定义，Phase 5 验证工具调用
- [[Plugin 扩展系统]] -- 插件注册新工具时使用 TypeBox 定义参数
- [[自我修改软件机制]] -- Agent 动态添加工具需要类型安全保障
- [[模型无关架构]] -- 同一份 Schema 适配多个 LLM Provider

## 参考

- [TypeBox GitHub](https://github.com/sinclairzx81/typebox)
- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
