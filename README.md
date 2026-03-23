# 🦞 OpenClaw Beginner Guide — 小白也能搭建 AI 机器人团队

> **零基础保姆级教程：从零开始，搭建你自己的 AI 团队**
> **小学生都能看懂！**

```
"AI 不应该是一个什么都干的超人，而应该是一支各有专长的团队。"
                                              — 阿圆 (Orion)
```

## 🤔 这是什么？

想象一下，你有一群 AI 机器人帮你干活：

- 🦞 **Miya** — 你的贴身管家，什么都能聊
- 💎 **David** — 天才程序员，写代码像玩一样
- 🎨 **Shenmu** — 艺术家，画画超好看
- 🌌 **Nova** — 产品经理，帮你规划项目
- 🔮 **Oracle** — 研究员，什么都能查到
- ✍️ **Steve** — 文案高手，写文章很厉害
- 🏛️ **Basaka** — 架构师，设计系统结构

**这个仓库记录了我怎么一步步把这个团队从 0 搭到 10 的全过程。**

每一篇笔记都用**小学生能听懂的方式**写成，有图有真相。

---

## 📖 学习笔记 (LearningNotes)

按时间顺序，每一篇都是我踩过坑之后的总结：

| # | 笔记 | 一句话说明 | 难度 |
|---|------|----------|------|
| 1 | [🧠 什么是多Agent？为什么需要它？](LearningNotes/01_what_is_multi_agent.md) | 从"一个人干所有活"到"组建专家团队" | ⭐ 入门 |
| 2 | [💰 怎么让 AI 又快又省钱？](LearningNotes/02_save_tokens_like_a_boss.md) | 不同的活用不同的脑子，贵的脑子只干贵的活 | ⭐ 入门 |
| 3 | [🛡️ 模型挂了怎么办？容灾保命指南](LearningNotes/03_model_failover.md) | 主力不行自动换替补，用户完全感觉不到 | ⭐⭐ 进阶 |
| 4 | [🧱 从零搭建完整系统](LearningNotes/04_build_from_scratch.md) | 安装、配置、启动，一步不漏的保姆教程 | ⭐⭐ 进阶 |
| 5 | [🤖 让 AI 自己学会不犯错](LearningNotes/05_self_improving_agent.md) | 犯错→自动记日记→下次自动翻日记→不再犯 | ⭐⭐⭐ 高级 |

---

## 🏗️ 项目架构

```
我的 AI 团队长这样：

     我（阿圆）
        │
        ▼
   ┌──────────┐
   │ Telegram  │  ← 我用手机发消息
   │  聊天群   │     远程遥控整个团队
   └────┬─────┘
        │
        ▼
   ┌──────────┐
   │ OpenClaw  │  ← 在我的 Mac 上运行
   │  Gateway  │     自动把消息分给对应的 AI
   └────┬─────┘
        │
   ┌────┼────┬────┬────┬────┬────┐
   ▼    ▼    ▼    ▼    ▼    ▼    ▼
  🦞   💎   🎨   🌌   🔮   ✍️   🏛️
 Miya David 神木 Nova Oracle Steve Basaka
  │    │    │    │    │    │    │
  ▼    ▼    ▼    ▼    ▼    ▼    ▼
 独立  独立  独立  独立  独立  独立  独立
 记忆  记忆  记忆  记忆  记忆  记忆  记忆
```

**每个 AI 有自己的脑子（模型）、性格（Prompt）、笔记本（记忆）和工具箱（权限）。**

互不干扰，就像一家公司里的不同部门。

---

## 📊 数字说话

| 指标 | 数值 |
|------|------|
| 核心 Agent | 10 个 |
| 工作流 Agent | 19 个 |
| 技能模块 | 36 个 |
| 已解决问题 | 45+ 个 |
| 日均省下的 Token | 约 50-70% |

---

## 🔧 技术栈

- **核心框架**：[OpenClaw](https://github.com/openclaw/openclaw)
- **通讯渠道**：Telegram Bot API
- **AI 模型**：DeepSeek V3.2 / MiniMax M2.7 / Gemini Flash
- **记忆系统**：LanceDB Pro (向量数据库 + 混合检索)
- **工作流引擎**：Antfarm (多Agent自动化流水线)
- **运行环境**：macOS (Apple Silicon)

---

## 🌟 受启发于

- [@Amyssjj](https://github.com/Amyssjj/Agent_Exploration) — Agent 原型探索
- [@win4r](https://github.com/win4r) — Claude Code Hooks / LanceDB Pro

---

## 📬 联系方式

如果你也在玩 OpenClaw，或者对多 Agent 系统感兴趣，欢迎交流！

---

*最后更新：2026-03-24*
