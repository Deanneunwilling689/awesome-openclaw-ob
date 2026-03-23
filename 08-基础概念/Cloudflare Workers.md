---
tags:
  - Cloudflare
  - 无服务器
  - 边缘计算
  - 部署
aliases:
  - Workers
  - Cloudflare Workers
  - moltworker
---

# Cloudflare Workers

## 一句话理解

> Cloudflare Workers 是运行在全球 300+ 边缘节点的无服务器计算平台——代码不在某台服务器上，而是在离用户最近的节点自动执行。Cloudflare 官方的 moltworker 项目让 OpenClaw 无需 VPS 即可直接部署在 Workers 上。

## 核心概念

### 什么是边缘计算

传统部署：用户请求 → 跨越半个地球 → 中心服务器处理 → 返回结果（延迟高）。
边缘计算：用户请求 → 最近的边缘节点处理 → 立即返回（延迟极低）。

Cloudflare Workers 基于 V8 引擎（与 Chrome 相同），在全球 300+ 数据中心运行 JavaScript/TypeScript 代码，冷启动时间接近零。

### moltworker：OpenClaw on Workers

Cloudflare 官方开源的 [moltworker](https://github.com/cloudflare/moltworker) 项目，将 [[OpenClaw 是什么|OpenClaw]] 部署到 Workers 平台。这是企业级整合的代表案例，与 DigitalOcean 1-Click Deploy、Fly.io 容器化部署并列为 OpenClaw 的三大云端部署方案。

### 与传统 VPS 部署的对比

| 维度 | VPS 部署 | Workers 部署（moltworker） |
|------|---------|--------------------------|
| 运维 | 需管理服务器、系统更新 | 零运维，Cloudflare 托管一切 |
| 扩展 | 手动扩容 | 自动全球分布 |
| 成本 | 固定月费（€5-28/月） | 按请求计费，有免费额度 |
| 延迟 | 取决于服务器地理位置 | 全球边缘，延迟最低 |
| 持久化 | 本地磁盘 | 需配合 KV/R2 等存储服务 |

## 应用与影响

- **降低部署门槛**：非技术用户无需管理 VPS，Workers 的零运维特性与 [[白手套部署服务]] 的理念一致
- **企业级信号**：Cloudflare 作为全球最大的 CDN/安全提供商之一，官方支持 OpenClaw 说明了 Agent 生态的战略价值
- **安全优势**：Workers 默认在隔离的 V8 沙箱中运行，天然比裸 VPS 部署更安全
- **局限性**：Workers 的执行时间限制（免费版 10ms CPU）和内存限制可能不适合长时间运行的 Agent 任务

## 关键洞察

moltworker 代表了一个重要趋势：**基础设施巨头主动拥抱 AI Agent 部署**。Cloudflare Workers、DigitalOcean 1-Click、Fly.io 容器化——这些不是社区的边缘实验，而是企业级云平台对 Agent 时代的基础设施投资。OpenClaw 的 [[模型无关架构]] 让它成为这些平台的天然合作伙伴。

## 外部链接

- [Cloudflare Workers 官方文档](https://workers.cloudflare.com)

## 双链导航

- [[OpenClaw 是什么]] — moltworker 部署的目标框架
- [[Docker 容器化]] — 另一种部署/沙箱方案
- [[模型无关架构]] — Workers 部署中仍可自由切换 LLM
- [[白手套部署服务]] — Workers 进一步降低部署门槛
- [[TypeScript]] — Workers 和 OpenClaw 共用的核心语言
