# BATCH-XX · <Batch 名称>

> 单 Batch 任务书模板。每个 Batch 拷一份本文件改名为 `BATCH-XX-<short-name>.md`。
> 启动前必须由用户审定。完工后冻结，不再改。

---

## 1. 推进的顶层意图

<本 Batch 完成后，docs/01-vision.md 哪条顶层意图变得"可验证"？>

例：
> Intent #1 「读者能从第一章追读到结局」——本 Batch 完成后，已产出完整第一章 + 通过风格/情节审查。

---

## 2. 验收意图（Definition of Done）

<本 Batch 完成的具体可验证标准。≥ 1 条可验证。>

例：
- [ ] 产出第一章正文 ≥ 3000 字
- [ ] 通过风格一致性检查（Q-001）
- [ ] 通过章节完整性检查（Q-002）
- [ ] 质量契约全部通过

---

## 3. 依赖

- **前置 Batch**：B<X>, B<Y>（必须 completed）
- **不依赖**：B<Z>（可与其并行）

---

## 4. 子任务清单

| 子任务 | 产出物 / 模块 | 子代理模板 | 并行 |
|--------|--------------|------------|------|
| <名称 1> | `<path>/<...>` | T2 | ✓ |
| <名称 2> | `<path>/<...>` | T2 | ✓ |
| <名称 3> | `<path>/<...>` | T3 | |

> **并行度**：本 Batch 推荐 N 个 agent 并行（理由：<...>）。

---

## 5. 硬约束（Batch 特定）

<不在 CLAUDE.md 通用硬约束里、但本 Batch 特别要注意的。>

例：
- 本 Batch 涉及外部 API 调用，必须先验证 API 可用性
- 本 Batch 改动核心模块，必须保留旧版备份
- ...

---

## 6. 验收命令

```bash
<跑质量检查的具体命令清单。复制粘贴可运行。>

例：
cd <项目根>
python scripts/check-style.py
python scripts/check-completeness.py
python scripts/wordcount.py
```

---

## 7. 完成后必做

- [ ] 更新 `PROGRESS.md`：本 Batch 状态置 `completed` + 完成时间 + 关键产出 / 踩坑
- [ ] 必要时追加 `DECISIONS.md`（新决策 / 偏离规格的记录）
- [ ] 如果本 Batch 关联 INTENT-GRAPH 中某条意图，回写 §3 对账表把状态置 `implemented`（Phase 3 起）
- [ ] 报告本批摘要 + 下一批编号给用户

---

## 8. 风险与已知问题

<本 Batch 已知的风险 / 待澄清。如已记入 DECISIONS.md，引用决策记录编号。>

例：
- 某依赖服务不稳定，本 Batch 先做 mock；真实对接在 B<X>（D-XXX 待澄清）
- ...
