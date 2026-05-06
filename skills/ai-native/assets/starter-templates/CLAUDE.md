# <项目名> · Claude 项目上下文

> 这份文件每个 Claude Code 会话自动加载。**项目纪律的唯一权威源**。
> 模板填法见末尾"如何使用本模板"。

---

## 必读

**每个新 session 的第一件事**：读 `EXECUTION.md`（仓库根）和 `docs/execution/PROGRESS.md`，按里面的纪律办事。

---

## 项目一句话

<在这里写：项目是什么 + 给谁用 + 解决什么核心问题。≤ 30 字。>

例：
> AI 小说生成工具，给独立作者用，解决"想写完一本书但写不下去"的问题。

---

## 顶层意图（来自 docs/01-vision.md）

<把 docs/01-vision.md 里 ≤ 5 条顶层意图的标题列在这里，作为 Claude 每次会话的"为什么做这个"提示。>

例：
1. 作者能从 0 写完一本 ≥ 10 万字的完整小说
2. 作品质量稳定且可观测
3. AI 成本对作者透明可控

---

## 硬约束（忘了会出事）

<这一段在 Phase 1 起草时填。每条都必须能在某条决策记录找到理由——指向 DECISIONS.md 编号。>

例：
1. **章节格式统一**：所有章节必须包含标题 + 正文 + 字数统计（D-002）
2. **风格一致性**：同一作品内叙述视角、时态、人称必须一致（D-004）
3. **规格默认只读**：`docs/0X-*.md` 默认不要改，例外条件见 D-XXX
4. **未知信息先查**：不确定的事实/数据先查证，别靠记忆编造

---

## 协作模式：Agent Team

Claude Code 支持 Agent Team（多 Agent 协同 + 共享 TaskList）。**默认用 Team 完成跨模块 / 多步任务**。

触发场景：
- 跨模块执行（同一 Batch 要动多个独立模块）
- 可并行的独立工作（不同维度、不同模块）
- 多步骤任务（研究 → 规划 → 执行 → 校验）

标准流程：
1. `TeamCreate` 建 team
2. `TaskCreate` 拆解 Batch 内子任务
3. `Agent` 派 teammate（按领域选择 agent 类型）
4. `TaskUpdate` 用 `owner` 指派给 teammate
5. teammate 完成会自动回消息，**不要轮询**
6. 收尾：`SendMessage shutdown_request` → `TeamDelete`

并行度纪律：
- Phase 2 核心链路：3-5 个 agent
- Phase 3 实施意图卡：3-5 个 agent
- 独立子任务：可达 5-9
- 已有项目改已有资产：1-2 + review agent

不开 team：单任务改 / 纯查询 / Phase 0 / 已无质量契约的项目。

---

## 工具链

<在这里写已确定的工具链/方法论选型。每个选型 + 理由都应该在 DECISIONS.md 有决策记录。>

例（软件开发）：
- Python 3.12 + FastAPI + SQLAlchemy 2 async + Pydantic v2
- PostgreSQL 16 + Redis 7
- 测试：pytest + pytest-asyncio
- 质量：ruff + mypy --strict + pre-commit

例（写作）：
- 写作引擎：Claude Opus 4（创意草稿）+ Claude Sonnet 4（编辑审校）
- 章节管理：Markdown + frontmatter
- 风格检查：自定义 style-guide.md + AI 审校
- 版本管理：Git + 每章独立文件

---

## 路线图

<在这里写：当前在哪个 Phase。路线图 ≤ N 个 Batch，详见 docs/execution/PROGRESS.md。>

例：
> 当前 Phase 2，B0-B9 共 10 个 Batch；核心验收意图："作者能创建作品 → 生成完整章节 → 导出成品"。

---

## 规划范式

<这一段在 Phase 3 启用 INTENT-GRAPH 时加进来。Phase 0/1/2 期间删掉本节即可。>

核心产出已落地后，未实现的需求改走**意图驱动 + Living Spec**，文件在 `docs/execution/INTENT-GRAPH.md`。

**规则**：
- 用户问"X 要不要做" → **不要直接开 Batch**。先看 INTENT-GRAPH 有无对应意图卡；有则评估证据、无则先写成意图卡
- 完成任何 Batch 时，需回写 INTENT-GRAPH §3 对账表
- 收到关于未实现入口的真实信号时，把对应意图从 `pending` 升 `probing`
- 检测到证伪条件命中时，状态置 `falsified`，并按决策流程反向修剪规格

**禁止**：
- 把 INTENT-GRAPH 当传统规格（不写人天 / deadline / 甘特图）
- 不带证据 + 没有 user override 就升 `validated`
- 用主观词写证伪条件

---

## 语言

<在这里写：会话语言、记录语言、产出物语言。>

例：
> 回复和记录用简体中文；产出物（章节/代码/设计稿）语言按项目需要。

---

## 如何使用本模板

1. 把每段 `<...>` 占位符替换成项目实际内容
2. 删掉所有"例：" 段（那些只是参考）
3. Phase 0/1/2 期间"规划范式"段可以先删；Phase 3 启用时加回来
4. 任何硬约束新增 / 修改都必须先在 DECISIONS.md 立决策记录，再回填本文件
