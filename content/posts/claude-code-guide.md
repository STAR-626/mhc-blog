---
title: "Claude Code 入门指南——让 AI 帮你写代码"
date: 2026-05-15
description: "从安装配置到日常使用，一文讲清楚如何用 Claude Code 提高编程效率。包含 MCP 工具配置、浏览器自动化等实用技巧。"
tags: ["AI", "Claude Code", "教程"]
---

## 什么是 Claude Code

Claude Code 是 Anthropic 推出的终端 AI 编程助手。和普通的 AI 聊天不同，它能**自主规划任务、调用工具、读写文件、执行命令**——相当于一个能自己干活的工程队队长，而不只是听一句做一句的工人。

## 安装与配置

首先确保你安装了 Node.js（18+ 版本），然后：

```bash
npm install -g @anthropic-ai/claude-code
```

安装完成后，在终端输入 `claude` 即可启动。首次使用需要配置 API Key：

```bash
export ANTHROPIC_API_KEY="your-api-key-here"
claude
```

> 如果你用的是 DeepSeek 等第三方 API，可以通过 settings.json 中的 proxy 字段配置自定义端点。

## 核心功能

### 1. Agent 自主干活

你可以直接说「帮我在这个项目里加一个登录功能」，Claude Code 会自己拆任务、读代码、写代码、跑测试，全程不用你一步步指挥。

### 2. MCP 工具生态

MCP（Model Context Protocol）是 AI 的「USB-C 接口」——通过 MCP 服务器，Claude Code 可以：

- 操控浏览器（Playwright MCP）——自动填表、截图、爬取动态网页
- 连接数据库（PostgreSQL、SQLite 等）
- 读写文件系统
- 调用外部 API

配置 Playwright MCP 的 `mcp.json` 示例：

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

### 3. 记忆系统

Claude Code 支持持久化记忆（MEMORY.md），可以记住你的偏好、项目背景和常用配置，越用越懂你。

### 4. Skills 和 Hooks

你可以自定义技能（Skills）让 AI 执行特定领域任务，也可以通过 Hooks 在特定事件（如工具调用前后）自动触发脚本。

## 实用技巧

- **用 `/fast` 切换快速模式**：在不影响质量的前提下加速输出
- **善用 `/memory`**：把重要的上下文存成记忆，下次对话自动加载
- **批量操作**：AI 可以同时执行多个独立操作，效率翻倍
- **搭配 Obsidian**：把 Claude Code 的对话记录导出到知识库，形成长期积累

## 总结

Claude Code 是目前最强的终端 AI 编程工具之一。它不只是一个聊天 bot，而是一个能真正帮你干活的 AI 搭档。从写代码到操控浏览器，从管理知识库到自动化工作流，它会成为你电脑上最有用的工具之一。
