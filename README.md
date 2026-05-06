# AI-Native 工作流元框架

> AI-Native 的**元框架**——用于创建领域特定的 AI-native 工作流 skill（如 AI-Native-Code、AI-Native-Write）。

本仓库不是直接用于项目执行的终端工具。它提供 4-Phase 骨架、质量契约网络、INTENT-GRAPH 和 Agent Team 规范，供你派生自己的领域工作流 skill。

**类比**：如果 `skill-creator` 是创建 Claude Code skill 的工具，那么 `ai-native` 就是创建 AI-native 工作流 skill 的元框架。

## 你应该用什么

| 你的需求 | 用哪个 |
|----------|--------|
| 我想做软件开发项目 | → [`AI-Native-Code`](https://github.com/tianji-qingtian/AI-Native-Code) |
| 我想写小说 | → AI-Native-Write（待建） |
| 我想创建一个新领域的 AI-native 工作流 | → **本仓库** |

## 文件一览

| 文件 | 内容 |
|------|------|
| [`AI-Native-通用方法论.md`](AI-Native-通用方法论.md) | 方法论本体：4-Phase 骨架 + 领域特化接口 + 参考实现 |
| [`skills/ai-native/`](skills/ai-native/) | Claude Code skill：引导派生新领域工作流 skill |

## 我要创建新领域的 AI-native 工作流

安装本 skill：

```bash
cp -r ./skills/ai-native ~/.claude/skills/ai-native
```

在 Claude Code 中说：

```
我想为 <领域名> 创建一个 AI-native 工作流 skill，参照 AI-Native-Code 的结构
```

Claude 会引导你完成领域特化接口定义（§2）、SKILL.md 编写、starter 模板定制。

完整创建流程见 `skills/ai-native/SKILL.md` §3。

## 关键原则

1. **AI 不是自主，是受约束的局部规划**——人类负责方向判断、不可逆决策、验收
2. **Phase 0/1 不能纯意图驱动**——AI 没素材可推
3. **质量契约网络是真相源**——静态文档会腐烂，自动化检查不会
4. **项目纪律入仓库（不入 memory）**——memory 绑机器，仓库走分发
5. **INTENT-GRAPH 是 Phase 3 工具**——核心产出落地前不写意图卡

---

> **AI 是强大的执行者，但权力和责任必须留在人手里，而契约是连接两者的唯一可靠桥梁。**

## 已派生的领域工作流

| 变体 | 仓库 | 说明 |
|------|------|------|
| AI-Native-Code | [GitHub](https://github.com/tianji-qingtian/AI-Native-Code) | 软件开发特化版（mypy/pytest/importlinter 等） |
| AI-Native-Write | 待建 | 小说/写作特化版 |
| AI-Native-Design | 待建 | 设计创作特化版 |

## 反馈与版本

- v0.2（2026-05-06）：重新定位为元框架，从 AI-Native-Code 提取并通用化
- 每次新派生一个领域工作流后更新
