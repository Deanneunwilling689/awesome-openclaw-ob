---
title: SQLite
aliases: [SQLite 数据库, 嵌入式数据库, SQLite 持久化, OpenClaw 数据层, sqlite-vec, FTS5, SQLite 数据存储]
category: 技术基础
tags: [database, SQLite, storage, embedded, local-first, sqlite-vec, FTS5, 向量搜索, 持久化, 记忆系统, OpenClaw]
created: 2026-03-14
updated: 2026-03-14
---

## SQLite 是什么

想象一个数据库，不需要安装、不需要启动服务、不需要配置端口——它就是一个文件。复制这个文件就是备份，删除这个文件就是卸载。**SQLite 就是装在口袋里的数据库。**

它是全世界部署最广泛的数据库引擎：每台 iPhone、每台 Android 手机、每台 Mac、每个浏览器里都有它。全球有数万亿个 SQLite 数据库在运行。它不是"轻量替代品"，它本身就是标准。

## 为什么是 AI Agent 的理想存储

| 需求 | SQLite 的回答 |
|------|-------------|
| 零配置 | 无服务器进程，无端口，无后台进程 |
| 可移植 | 整个数据库就是一个 `.sqlite` 文件，拷走即用 |
| 本地优先 | 数据不出设备，天然满足隐私要求 |
| 高性能 | 现代 NVMe SSD 上可达 50万+ 随机 IOPS，延迟 < 100μs |
| 生态丰富 | FTS5（全文搜索）、sqlite-vec（向量搜索）提供完整 RAG 能力 |

2026年 SQLite 正在经历"文艺复兴"：Turso、Cloudflare D1、LibSQL、Litestream 等项目解决了它的历史局限（单写者、无复制），同时保留了它的简单性。

## OpenClaw 如何用 SQLite

OpenClaw 的整个[[记忆系统|记忆系统]]建立在 SQLite 之上，存储于 `~/.openclaw/memory/<agentId>.sqlite`，由 TypeScript 代码驱动：

### 混合搜索评分

| 扩展 | 作用 | 权重 |
|------|------|------|
| **sqlite-vec** | 向量相似度搜索（余弦相似度） | 70% (vectorWeight: 0.7) |
| **FTS5** | BM25 关键词全文检索 | 30% (textWeight: 0.3) |

评分公式：`finalScore = vectorWeight * vectorScore + textWeight * textScore`

### 五层数据职责

1. **记忆索引**：Markdown 知识文件被分块、嵌入后，索引存入 `.sqlite` 文件
2. **向量搜索**：通过 sqlite-vec 扩展存储和查询嵌入向量，执行余弦相似度计算
3. **全文搜索**：通过 FTS5 扩展实现 BM25 关键词检索
4. **嵌入缓存**：缓存已生成的嵌入向量，避免重复调用嵌入API
5. **会话持久化**：[[会话管理|会话数据]]以 JSONL 格式存储，但索引由 SQLite 管理

### 配合记忆系统三层结构

- **MEMORY.md**：策划的稳定事实，SQLite 索引其内容以便向量检索
- **每日笔记** `memory/YYYY-MM-DD.md`：运行中的活动日志
- **会话转录索引**：全历史可搜索性

核心设计哲学：**Markdown 是数据源头（source of truth），SQLite 是检索加速器**。删了 SQLite 文件？没关系，从 Markdown 重建就行。

## 与服务端数据库的对比

| 维度 | SQLite | PostgreSQL / pgvector |
|------|--------|----------------------|
| 部署 | 零配置，进程内 | 需要安装、配置、维护 |
| 适用场景 | 单用户 Agent、本地优先 | 多用户、企业级、云部署 |
| 向量搜索 | sqlite-vec（够用） | pgvector（更成熟） |
| 并发写入 | 单写者模型 | 多写者支持 |
| 备份 | 复制文件 | pg_dump 或流复制 |

对于 OpenClaw 这样的个人 AI Agent，SQLite 是过度工程的反面——它恰好够用，而且简单到不会出错。

## 关键洞察

SQLite 是 OpenClaw [[AI 基础设施思维|基础设施哲学]] 的完美体现——不追求技术复杂度，而是选择"恰好够用且不会出错"的方案。sqlite-vec + FTS5 的混合搜索让一个文件就能提供完整的 [[向量嵌入与混合搜索|RAG]] 能力，这正是 OpenClaw 能"零依赖部署"的技术基石。但单写者模型也意味着并发写入受限——这是 [[自主决策循环|Lane-Based Queuing]] 需要"单写者规则"的数据层原因。

## 外部链接

- [SQLite 官方网站](https://sqlite.org)

## 相关笔记

- [[记忆系统]] —— SQLite 是记忆系统的存储后端
- [[向量嵌入与混合搜索]] —— 向量索引和 FTS5 索引都住在 SQLite 里
- [[OpenClaw 是什么]] —— 本地优先架构的基石
- [[会话状态管理|会话管理]] —— 会话数据的持久化机制
- [[AI 基础设施思维]] —— 本地优先架构的设计哲学
- [[Ollama 本地模型运行]] —— 本地存储 + 本地推理 = 完全离线
- [[Supabase]] —— 云端数据库方案，与 SQLite 本地优先形成互补对比
