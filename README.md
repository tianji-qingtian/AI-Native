# AI-Native 通用工作流

> AI-native 工作的通用方法论——核心不是"让 AI 自主"，是让多 Agent 在共享契约下并行干活。

适用于任何创造性领域：软件开发、小说写作、设计创作、学术研究、视频制作等。

包含：

- **4-Phase 通用框架**：意图凝练 → 契约骨架 → 质量契约网络 → 意图驱动多 Agent
- **两种场景**：空项目（前瞻）/ 已有资产（考古）
- **领域适配指南**：软件开发 / 写作 / 设计 / 研究 / 视频 的映射表
- **通用项目 starter**：`cp -r` 即用
- **反模式速查表**：踩过的坑都写在里面，别再踩
- **真实加速幅度**：30-50% / 10-30%，按场景给数，不吹 10x

适用读者：用 Claude Code（或同类 AI agent CLI）作为主力工具的创作者/工程师/研究者。
只想偶尔让 AI 改点东西的，这套方法论成本不回本。

## 文件一览

| 文件 | 内容 |
|------|------|
| [`AI-Native-通用方法论.md`](AI-Native-通用方法论.md) | 方法论本体：4-Phase 框架 + 空项目/已有资产两种场景 + 领域适配 + 反模式速查 |
| [`skills/ai-native/`](skills/ai-native/) | Claude Code skill：方法论的可执行版本，Claude 自动加载并引导 4-Phase 流程 |
| [`starters/generic-project/`](starters/generic-project/) | 通用项目 starter 模板，可直接 `cp -r` 起新项目 |

## 快速使用

### 安装 skill（一次性）

要把这套方法论用到你自己的项目（无论新项目还是已有项目），先把 skill 装到用户级目录：

```bash
cp -r ./skills/ai-native ~/.claude/skills/ai-native
```

装完后，在任何项目里启动 `claude`，skill 都会自动加载。

### 我要开新项目

在**空目录**里启动 Claude Code，说：

```
我想做一个 <你的 idea>，用 AI-native 方式启动
```

Claude 会引导 Phase 0（意图凝练）→ Phase 1（契约骨架）→ Phase 2（核心产出 + 质量契约）→ Phase 3（意图驱动）。

**或者手动拷贝模板**（不依赖 skill）：

```bash
cp -r ./starters/generic-project /path/to/new-project
cd /path/to/new-project
git init && git add . && git commit -m "feat: 项目初始化"
claude
> 帮我做 Phase 0：意图凝练。我想做一个 <你的 idea>
```

详见 [`starters/generic-project/README.md`](starters/generic-project/README.md)。

### 我要把这套方法论用到已有项目

在**已有项目目录**里启动 Claude Code，说：

```
用 AI-native 方式接入这个项目
```

Claude 会引导 Phase 0（考古：扫描项目、标注隐性约束）→ Phase 1（反推意图）→ Phase 2（建质量契约网络）→ Phase 3（增量挂意图卡）。

## 关键原则

1. **AI 不是自主，是受约束的局部规划**——人类负责方向判断、不可逆决策、验收
2. **Phase 0/1 不能纯意图驱动**——AI 没素材可推
3. **质量契约网络是真相源**——静态文档会腐烂，自动化检查不会
4. **项目纪律入仓库（不入 memory）**——memory 绑机器，仓库走分发
5. **INTENT-GRAPH 是 Phase 3 工具**——核心产出落地前不写意图卡

---

> **AI 是强大的执行者，但权力和责任必须留在人手里，而契约是连接两者的唯一可靠桥梁。**

## 与其他 AI-Native 变体的关系

本仓库是 AI-Native 方法论的**通用骨架**。领域特化版本：

| 变体 | 仓库 | 说明 |
|------|------|------|
| AI-Native-Code | `../AI-Native-Code/` | 软件开发特化版（含 mypy/pytest/importlinter 等） |
| AI-Native-Write | 待建 | 小说/写作特化版 |
| AI-Native-Design | 待建 | 设计创作特化版 |

## 反馈与版本

- v0.1（2026-05-06）：初版，从 AI-Native-Code 提取并通用化
- 每次跨领域试点出口（成立 / 失败）后更新
