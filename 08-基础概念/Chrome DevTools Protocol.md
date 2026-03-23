---
title: Chrome DevTools Protocol
aliases: [CDP, Chrome调试协议]
category: 技术基础
tags: [CDP, browser-automation, chrome, devtools, web-automation]
created: 2026-03-14
updated: 2026-03-14
---

## CDP 是什么

每次你按下 F12 打开浏览器开发者工具，背后其实有一根"隐形电话线"连接着你的操作面板和浏览器内核。**CDP 就是这根电话线的通话协议**——它让程序可以像人按 F12 一样，控制浏览器的一切：导航页面、点击按钮、截图、拦截网络请求。

本质上，CDP 是一个基于 JSON-RPC 的 WebSocket 双向通信协议。客户端发命令，浏览器执行并返回结果，同时浏览器也会主动推送事件（比如"页面加载完了"）。

## 核心能力

CDP 暴露了约 300 个命令，按**域（Domain）**组织：

| 域 | 能力 | Agent 用途 |
|----|------|-----------|
| **Page** | 导航、截图、PDF生成 | 访问网页、获取页面快照 |
| **DOM** | 查询/修改 DOM 节点 | 读取页面内容、填写表单 |
| **Network** | 请求拦截、修改响应 | 监控 API 调用、注入数据 |
| **Runtime** | 执行 JavaScript | 在页面上下文中运行任意代码（涉及代码执行安全） |
| **Input** | 模拟键盘/鼠标事件 | 点击、输入、拖拽 |
| **Emulation** | 设备模拟、地理位置 | 模拟移动设备、切换语言 |

## OpenClaw 的浏览器控制

[[OpenClaw 是什么|OpenClaw]] 通过 **Browser Relay** 组件基于 CDP 实现浏览器自动化，运行在端口 18792，提供三种模式：

1. **Extension Relay**：控制你已经打开的 Chrome 标签页（保留登录状态）
2. **OpenClaw-managed**：启动独立的隔离浏览器实例（类似沙箱隔离）
3. **Remote CDP**：连接远程/云端浏览器，适合分布式部署（可配合Docker 容器化）

Browser Relay 把原始的 CDP WebSocket 命令封装成简洁的 HTTP/CLI 接口。AI Agent 说"点击元素12"，Relay 翻译成对应的 CDP 操作。这和 Puppeteer/Playwright 的设计哲学一致——在低层协议之上构建人性化的 API。

## 与 Selenium/Playwright 的对比

| 维度 | CDP（原生） | Selenium WebDriver | Playwright |
|------|-----------|-------------------|------------|
| 通信方式 | WebSocket 双向 | HTTP 单向 | CDP + 自有协议 |
| 浏览器支持 | 仅 Chromium 系 | 全部主流浏览器 | Chromium/Firefox/WebKit |
| 延迟 | 最低（直连内核） | 较高（多层代理） | 低 |
| 能力深度 | 完整（300+ 命令） | 标准化子集 | 接近 CDP 的完整性 |
| AI Agent 适配 | 需自行封装 | 过重 | 较好但体积大 |

未来方向：**WebDriver BiDi** 正在统一 CDP 的双向通信优势和 WebDriver 的跨浏览器兼容性。

## 安全隐患

CDP 赋予 Agent 强大的浏览器控制能力，但也引入了[[安全边界与风险（总览）|安全风险]]：Agent 可通过 Runtime 域执行任意 JavaScript，Network 域拦截修改请求。这意味着恶意 Prompt Injection 可能诱导 Agent 通过 CDP 执行有害操作，例如窃取页面中的登录凭证或敏感数据。合理的权限控制机制和[[Tool Use 机制|工具调用]]审批流程至关重要。

## 实际案例

在 [[案例-Tesco 超市自动购物]] 中，OpenClaw 通过 CDP 控制浏览器登录超市网站、浏览商品、加入购物车、完成结算——整个过程无需人工干预。在 [[案例-汽车购买谈判省4200美元]] 中，Agent 能自动浏览经销商网站、比较价格、甚至通过表单发起谈判。

## 外部链接

- [Chrome DevTools Protocol 官方文档](https://chromedevtools.github.io/devtools-protocol/)

## 相关笔记

- [[OpenClaw 是什么]] —— Browser Relay 是 OpenClaw 的核心能力之一
- [[OpenClaw v2026.3 版本更新]] —— v2026.3.22-beta.1 增强了浏览器自动化（批量操作、选择器定位、Chrome DevTools MCP）
