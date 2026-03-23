# 🔧 技能与 MCP 扩展

> OpenClaw 的 Skill（技能）和 MCP（模型上下文协议）配置技巧

---

## 什么是 Skill？

**Skill = AI 的专业工具。**

比喻：AI 本身很聪明，但没有工具什么也干不了——就像一个天才厨师，没有刀和锅也做不了菜。

Skill 就是给 AI 的"工具"。

| Skill 举例 | 干什么 |
|-----------|--------|
| 即梦生图 | 调用即梦 API 画画 |
| 浏览器自动化 | 打开网页、截图、操作 |
| 文件操作 | 读写文件、执行脚本 |
| Dispatch | 把任务分配给其他 AI |

---

## 什么是 MCP？

**MCP = Model Context Protocol = AI 和外部工具的"翻译官"。**

普通情况：AI 不知道怎么调用外部工具
有了 MCP：AI 可以通过统一的协议调用任何工具

```
AI 想要搜网页
      │
      ▼
  ┌──────────┐
  │   MCP     │  ← 翻译官
  │  Server   │     把 AI 的请求翻译成工具能听懂的语言
  └─────┬────┘
        │
        ▼
  🌐 Exa 搜索引擎
  📄 Markitdown
  🎵 NotebookLM
  🖥️ Chrome DevTools
```

---

## 我在用的 MCP 工具

| MCP Server | 干什么 | 日常使用频率 |
|-----------|--------|------------|
| Chrome DevTools | 操控浏览器 | ⭐⭐⭐⭐⭐ |
| Exa | 搜网页 | ⭐⭐⭐⭐ |
| Context7 | 查最新技术文档 | ⭐⭐⭐ |
| Playwright | 浏览器自动化测试 | ⭐⭐⭐ |
| Markitdown | 把网页转成文本 | ⭐⭐ |
| NotebookLM | 知识库管理 | ⭐⭐ |
| Supabase | 数据库操作 | ⭐⭐ |

---

## 怎么装 MCP？

以 Chrome DevTools 为例：

```bash
# 1. 在 MCP 配置文件里加一条
~/.gemini/antigravity/mcp_config.json

# 2. 加这段配置：
{
  "chrome-devtools": {
    "command": "npx",
    "args": ["-y", "chrome-devtools-mcp@latest"]
  }
}

# 3. 重启你的 AI 工具
```

---

## 自定义 Skill

你可以写自己的 Skill！比如一个"每日天气播报"技能：

```
~/.openclaw/skills/weather-report/
├── SKILL.md         ← 技能说明书
├── scripts/
│   └── get_weather.sh  ← 执行脚本
└── examples/
    └── sample.md    ← 使用示例
```

`SKILL.md` 的格式：

```yaml
---
name: Daily Weather Report
description: 获取指定城市的天气预报
---

# 使用方法
执行 scripts/get_weather.sh 并传入城市参数
```

---

*更多 Skill 开发指南参见 OpenClaw 官方文档*
