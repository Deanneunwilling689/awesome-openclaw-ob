---
tags:
  - 安全
  - OpenClaw
  - 安全模型
  - 官方
aliases:
  - OpenClaw安全设计
  - 官方安全模型
---

# OpenClaw 官方安全模型

OpenClaw 官方承认：**"没有'完美安全'的设置"**。

## 安全架构

### 信任模型
- 每个网关**一个受信操作者**
- 不支持多对抗性用户共享同一网关
- 基于 TOFU（Trust On First Use）策略（CVE 修复后引入）
- 这一设计与 [[致命三合一安全矛盾]] 中描述的根本矛盾密切相关

### 沙箱
- Docker 容器隔离（**默认关闭**，需手动开启）
- 详见 [[沙箱机制]]

### DM 配对
- 未知发送者收到配对码
- 需人工批准才能建立信任

## 已知安全缺陷

1. **沙箱绕过**：工具策略绕过 + TOCTOU 竞态条件（约 25% 暴力成功率）
2. **[[ClawJacked 远程代码执行漏洞]]**：已修复但暴露了架构问题
3. **[[Prompt Injection 风险]]**：无法从架构层面解决（大语言模型的固有缺陷）

## 核心矛盾

这与 OpenClaw 安全风险 和 [[ClawHavoc 事件]] 揭示的问题一脉相承。恶意 Skills 供应链攻击更是在 Skills 市场层面放大了这一矛盾。

```
安全性 ←────────────────→ 实用性
越多的访问权限 = 越有用 = 越危险
```

> Aikido.dev："全面强化基本上把它变成了带额外编排的 ChatGPT。**它只在危险时才有用**。"

## 相关笔记

- [[安全边界与风险（总览）]]

## 参考

- [OpenClaw GitHub](https://github.com/anthropics/openclawx)
- [OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
