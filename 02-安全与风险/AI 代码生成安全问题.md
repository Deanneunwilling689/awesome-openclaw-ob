---
tags:
  - 安全
  - AI编码
  - 风险
aliases:
  - AI代码安全
  - Veracode报告
---

# AI 代码生成安全问题

Veracode 2025 年报告揭示了 [[Agentic Coding|AI 代码生成]]的系统性安全隐患。这些问题与 [[AI Agent 安全现状]] 中 88% 组织报告安全事件的数据形成呼应。

## 核心发现

- **45% AI 生成代码样本**未通过安全测试（包含 OWASP Top 10 漏洞）
- Java 风险最高（安全失败率超 70%）
- Python/C#/JavaScript 失败率在 38-45% 之间

## 关键问题

LLM 在功能性代码生成上持续改进，但**安全性能一直没有提升**——这是系统性训练问题，不会随模型升级自动解决。即使 2026 前沿模型竞争格局 中的最新模型（Claude Opus 4.6、GPT-5.3）在编码基准上大幅进步，安全性改善仍然有限。

## 对 OpenClaw 生态的影响

- Vibe Coding 让更多非技术用户生成代码，但安全意识普遍不足
- [[OpenClaw 安全风险]] 中的安全债务问题与此叠加
- OpenClaw 生态系统商业机会 中安全服务（Snyk、Daytona）因此存在巨大市场空间

## 相关笔记

- [[AI 代码生成宏观数据]]
- [[OpenClaw 安全风险]]
- [[OpenClaw 投资风险因素]]
- [[安全边界与风险（总览）]]
- [[代码执行安全]]
- [[Prompt Injection 风险]]

## 外部链接

- [Snyk Blog - Code Security](https://snyk.io/blog/)
- [NIST AI](https://www.nist.gov/artificial-intelligence)
