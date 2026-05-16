---
title: "用 Playwright MCP 操控浏览器——自动化测试与爬虫"
date: 2026-03-20
description: "在 Claude Code 中配置 Playwright MCP，实现浏览器全自动操作——搜索、点击、截图、购物流程一气呵成。"
tags: ["自动化", "Playwright", "MCP"]
---

## 什么是 MCP

MCP（Model Context Protocol）是 AI 的"USB-C 接口"——通过标准化的协议，AI 可以直接调用外部工具。Playwright MCP 就是其中一个最实用的服务器，让 AI 能操控真实的浏览器。

## 配置步骤

在 Claude Code 的工作目录下创建 `mcp.json`：

```json
{
  "mcpServers": {
    "playwright": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@playwright/mcp", "--browser", "msedge"]
    }
  }
}
```

重启 Claude Code 后，MCP 工具自动加载。

## 核心能力

- **browser_navigate**：打开任何网页
- **browser_snapshot**：抓取页面结构（比截图更好用）
- **browser_click**：点击按钮、链接
- **browser_type**：在输入框里打字
- **browser_take_screenshot**：截图

## 实战演示：完整购物流程

我最近做了一次全自动购物 Demo：

- 打开电商网站 → 自动登录
- 浏览商品列表 → 选两个加入购物车
- 进购物车 → 点结算
- 填收货信息 → 到支付确认页

> 全程 0 次手动操作鼠标键盘，11 步自动化完成。

## 限制与对策

国内主电商平台（淘宝、京东）有严格反爬机制：

- **淘宝**：商品详情页强制跳登录
- **京东**：搜索触发风控验证
- **B 站、GitHub、SauceDemo**：丝滑无阻

实际可用场景：自动刷课签到、批量截图存档、爬 JS 渲染页面、测试自己的前端项目。
