# 通用项目 Starter（AI-Native 工作流）

> 一份从 0 启动新项目时可直接拷贝使用的目录骨架。配套方法论：
> [`../../AI-Native-通用方法论.md`](../../AI-Native-通用方法论.md)

---

## 快速开始

```bash
# 1. 拷贝骨架到新项目
cp -r ./starters/generic-project /path/to/your-new-project

# 2. 进入新项目并初始化 git
cd /path/to/your-new-project
git init
git add .
git commit -m "feat: 项目初始化（AI-native 工作流骨架）"

# 3. 启动第一个 Claude Code 会话
claude
> 帮我做 Phase 0：意图凝练。我想做一个 <你的 idea>
```

---

## 目录结构

```
your-new-project/
├── CLAUDE.md                              ← 项目纪律权威源（每个会话自动加载）
├── EXECUTION.md                           ← 续跑剧本（新会话第一件事读这个）
├── README.md                              ← 项目自身的 README（待填）
├── docs/
│   ├── 01-vision.md                       ← Phase 0 产出（顶层意图 ≤ 5 条）
│   ├── 02-architecture.md                 ← Phase 1 产出（项目架构）
│   ├── 03-quality-contract.md             ← Phase 1 产出（质量契约）
│   └── execution/
│       ├── README.md                      ← execution 目录索引
│       ├── PROGRESS.md                    ← Phase 2 路线图看板
│       ├── DECISIONS.md                   ← 决策日志
│       ├── INTENT-GRAPH.md                ← Phase 3 才启用的意图图谱
│       ├── AGENT-PROMPTS.md               ← 子代理 prompt 模板
│       └── BATCH-template.md              ← 单 Batch 任务书模板
└── .gitignore
```

---

## 4-Phase 路线图

| Phase | 输入 | 输出 | Claude Code 角色 |
|-------|------|------|-------------------|
| 0 · 意图凝练 | 自然语言愿景 | `docs/01-vision.md` | 反问者 + 起草者 |
| 1 · 契约骨架 | 顶层意图 | `CLAUDE.md` / `02-arch` / `03-quality` / `DECISIONS.md` 初版 | 起草者 |
| 2 · 核心产出 + 质量契约 | 架构骨架 | 核心链路产出物 + 质量契约 + Batch 历史 | 执行者（Agent Team） |
| 3 · 意图驱动 | 真实使用证据 | `INTENT-GRAPH` 状态流转 + 增量改进 | 执行者 + 对账者 |

---

## 适用于任何领域

本 starter 是**领域无关的骨架**。无论你做什么——软件开发、小说写作、设计创作、学术研究、视频制作——都可以用这套模板启动。

在 Phase 1 时，根据你的领域填写具体化的内容：
- **软件开发**：质量契约 → mypy/pytest/linter
- **写作**：质量契约 → 风格检查/情节校验/字数统计
- **设计**：质量契约 → 设计系统规则/无障碍检查
- **研究**：质量契约 → 引用完整性/数据溯源/论证逻辑

---

## 第一次启动该做什么

### 1. 在 Claude Code 里说

```
我准备做一个新项目（领域：<写作/设计/研究/代码/其他>），想法是：<5-15 句话描述你的 idea>

请按方法论 Phase 0 启动：先反问我至少 1 轮（关于动机、场景、受众行为），
然后起草 ≤ 5 条顶层意图填到 docs/01-vision.md，让我审。
不要开 Agent Team，Phase 0 只是凝练。
```

### 2. Phase 0 完成后说

```
顶层意图已定稿。请按 Phase 1 起草：
- CLAUDE.md（项目纪律 + 工具链选型理由）
- docs/02-architecture.md（项目架构）
- docs/03-quality-contract.md（质量契约）
- docs/execution/DECISIONS.md（≥ 5 条初始决策记录）

每个不可逆决策都要立决策记录。工具链备选先列再让我拍板。
```

### 3. Phase 1 完成后说

```
架构已定稿。请按 Phase 2 拆 ≤ 10 个 Batch：
- 每个 Batch 推进哪条顶层意图
- 严格依赖图
- 每个 Batch 的质量检查同步建

写到 docs/execution/PROGRESS.md，并给每个 Batch 起草 BATCH-XX-*.md。
我审完后我们开第一个 Batch。
```

---

## 关键纪律（最容易忘）

- **项目纪律入仓库，不入 memory**：memory 绑用户机器，仓库走分发
- **Phase 0/1 不要启用 INTENT-GRAPH**：会写空想意图
- **质量契约 Phase 1 就配，每 Batch 验证**：质量契约是真相源
- **每个 Batch 末尾人类必须验收**："AI 报告全绿"≠"真的对"
- **Agent Team 并行度看上下文风险**：不熟的领域从 2-3 开始
