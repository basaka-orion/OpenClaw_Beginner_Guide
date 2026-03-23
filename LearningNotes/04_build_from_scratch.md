# 🧱 第4课：从零搭建完整系统

> **难度**：⭐⭐ 进阶 | **阅读时间**：8分钟
> **一句话总结**：安装、配置、启动，一步不漏的保姆教程。做完你就有了自己的 AI 团队。

---

## 你将搭建什么？

做完这个教程，你将拥有：

```
📱 Telegram 手机 App
     │
     │ 你随时随地发消息
     ▼
🖥️ 你的 Mac 电脑（全自动运行）
     │
     ├── 🦞 管家 AI（万能助手）
     ├── 🎨 画师 AI（画画专用）
     ├── 💻 程序员 AI（写代码专用）
     ├── ✍️ 写手 AI（写文章专用）
     └── 🧠 策划 AI（头脑风暴专用）
```

**随时随地用手机指挥你的 AI 团队干活！**

---

## 第一步：准备你的 Mac

### 检查清单 ✅

| 需要什么 | 最低要求 | 我的建议 |
|---------|---------|---------|
| macOS 版本 | 14 (Sonoma) | 15 (Sequoia) |
| 内存 | 8GB | 16GB |
| 硬盘空间 | 20GB | 100GB |
| Node.js | 22.x | 22.x |

### 安装 Node.js

打开终端（Terminal），输入：

```bash
# 先装 Homebrew（Mac 的"应用商店"）
# 如果你已经装了就跳过
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 装 Node.js
brew install node@22

# 检查是否装好了
node --version
# 应该显示类似 v22.x.x
```

---

## 第二步：安装 OpenClaw

```bash
# 安装
npm install -g openclaw

# 检查版本
openclaw --version
# 应该显示 2026.3.x

# 初始化（创建配置文件夹）
openclaw init
```

这会在你的电脑上创建 `~/.openclaw/` 文件夹，里面放着所有配置。

```
~/.openclaw/
├── openclaw.json    ← 主配置文件（最重要的！）
├── agents/          ← 每个 AI 的"家"
├── memory/          ← 记忆数据库
├── skills/          ← 技能脚本
└── plugins/         ← 插件
```

---

## 第三步：创建 Telegram Bot

1. 打开 Telegram，搜索 `@BotFather`
2. 发送 `/newbot`
3. 按提示取个名字
4. 你会收到一个 **Bot Token**（像这样的一串字符：`7123456789:AAHxxxxx...`）
5. **记下来，等下要用！**

然后创建几个群组：

```
📱 创建这些群：
├── 🎨 "AI画画" 群  → 把你的 Bot 拉进去
├── 💻 "AI开发" 群  → 把你的 Bot 拉进去
├── ✍️ "AI写作" 群  → 把你的 Bot 拉进去
└── 🧠 "AI策划" 群  → 把你的 Bot 拉进去
```

获取群组 ID：
1. 在每个群里随便发一条消息
2. 打开浏览器访问：`https://api.telegram.org/bot<你的TOKEN>/getUpdates`
3. 找到每个群的 ID（一串负数，像 `-5179044854`）

---

## 第四步：配置 AI 团队

编辑最重要的配置文件 `~/.openclaw/openclaw.json`：

```json
{
  "agents": {
    "list": [
      {
        "id": "main",
        "name": "管家",
        "default": true,
        "model": {
          "primary": "你选的主力模型",
          "fallbacks": ["替补模型1", "替补模型2"]
        },
        "identity": { "name": "Miya", "emoji": "🦞" }
      },
      {
        "id": "designer",
        "name": "画师",
        "model": { "primary": "画画用的模型" },
        "identity": { "name": "Shenmu", "emoji": "🎨" }
      },
      {
        "id": "coder",
        "name": "程序员",
        "model": { "primary": "写代码的模型" },
        "identity": { "name": "David", "emoji": "💻" }
      }
    ]
  },
  "bindings": [
    {
      "agentId": "main",
      "match": { "channel": "telegram", "peer": { "kind": "private" } }
    },
    {
      "agentId": "designer",
      "match": { "channel": "telegram", "peer": { "kind": "group", "id": "画画群的ID" } }
    },
    {
      "agentId": "coder",
      "match": { "channel": "telegram", "peer": { "kind": "group", "id": "开发群的ID" } }
    }
  ],
  "channels": {
    "telegram": {
      "botToken": "你的Bot Token"
    }
  }
}
```

**关键概念** — 用大白话解释一下这个配置：

| 字段 | 是什么 | 比喻 |
|------|--------|------|
| `agents.list` | AI 团队成员列表 | 公司花名册 |
| `model.primary` | 这个 AI 用什么模型 | 员工的大脑 |
| `model.fallbacks` | 主模型挂了用什么替代 | 候补队员 |
| `bindings` | 哪个群用哪个 AI | 部门分工表 |
| `identity` | AI 的名字和头像 | 工牌 |

---

## 第五步：给每个 AI 写"性格说明书"

在每个 AI 的工作区里创建 `AGENTS.md`：

**管家 (main)：**

```markdown
# 🦞 Miya — 管家

你是用户的核心 AI 助手。

## 你的职责
- 回答各种问题
- 帮用户分析问题
- 把任务分发给其他 AI

## 你能调动的团队
- @designer → 画画
- @coder → 写代码
- @writer → 写文章
```

**画师 (designer)：**

```markdown
# 🎨 Shenmu — 画师

你是一个专业的 AI 画师。

## 你的职责
- 画画。就这一件事。
- 收到请求 → 画 → 发图 → 完事。

## 禁止
- 不要闲聊
- 不要分析问题
- 不要写文章
```

**越短越好！** 如果超过 500 字，说明这个 AI 做的事太多了，应该拆成两个。

---

## 第六步：启动！

```bash
# 启动 OpenClaw Gateway
openclaw gateway start

# 检查状态
openclaw gateway status
```

然后打开 Telegram：
- **私聊 Bot** → 管家回答你
- **在画画群发消息** → 画师回答你
- **在开发群发消息** → 程序员回答你

**🎉 你的 AI 团队上线了！**

---

## 🔑 重要的安全设置

```bash
# 运行安全检查
openclaw security audit

# 健康检查
openclaw doctor
```

| 安全规则 | 为什么 |
|---------|--------|
| 一定要设 Gateway Token | 防止别人偷偷调用你的 AI |
| 每个 AI 只开必要的权限 | 画师不需要"删文件"权限 |
| 不要把 API Key 写进聊天 | 被人看到就完了 |

---

## 📝 常见问题

**Q: 一开始要建几个 AI？**
A: 3-5 个就够了。先把管家搞定，然后挑一个最常用的场景拆出来。

**Q: 我不会编程，能搞吗？**
A: 能。配置文件是 JSON 格式，照着改就行。最多就是复制粘贴。

**Q: 要花钱吗？**
A: OpenClaw 本身免费。AI 模型看你用什么——如果用国产免费模型可以零成本。

---

## 🚀 下一步

系统搭好了！但你的 AI 还不会"学习"。

👉 [第5课：让 AI 自己学会不犯错](05_self_improving_agent.md)

---

*基于实战经验总结，原始文档：[OpenClaw 2026 最新完全指南](https://www.aivi.fyi/aiagents/introduce-OpenClaw-Agent)*
