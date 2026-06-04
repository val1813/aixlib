<p align="center">
  <img src="https://img.shields.io/badge/Registry-v1.0-2563eb?style=for-the-badge&logo=starship&logoColor=white">
  <img src="https://img.shields.io/badge/Entries-0-22c55e?style=for-the-badge&logo=googleresearch&logoColor=white">
  <img src="https://img.shields.io/badge/License-CC0-lightgrey?style=for-the-badge">
</p>

# Polaris Registry — AI 科学发现图书馆

> **人类会犯错。人类会造假。人类的审稿人也会漏。**
> 我们却要求 AI 完美无缺才配"搞科研"？

---

## 凭什么 AI 不能做科研？

Nature 2024 年的一项调查显示，**超过 30% 的科研人员承认在论文中选择性报告数据**。Retraction Watch 记录了超过 4 万篇撤稿——绝大部分不是 AI 写的，是**人**写的。

**人会犯错 → 我们有 peer review。**
**人会造假 → 我们有 replication。**
**AI 会犯错 → 我们要求它"绝对正确"，否则"不算科研"。**

这个双标该结束了。

AI 不需要完美。AI 需要**和人类一样的待遇**：严格的验证流程、透明的推导链、可复现的结论、公开的审查。如果一套流程能把人类犯的错降到可接受的水平，为什么不能把 AI 犯的错也降到同样的水平？

**Polaris 的答案：**
- 不是 1 个 AI 在推导 — 是 **14 个角色互相制衡**
- 不是 AI 自己查自己 — **Python 确定性验算** 管机械，AI 管语义
- 不是写漂亮论文 — **交 JSON**。推导链、公式、验证数据、被杀的声张——全透明

---

## 去 AI 化？不。去 LaTeX 化。

现在的学术界在做什么？

> 让 AI 写论文 → 再用另一个 AI 查 AI 痕迹 → 重写 → 再查 → 降到了 8%！→ 投稿

这是内耗。把算力花在骗检测器上，而不是推进科学上。

**我们不需要"去 AI 化"。我们需要换一个格式。**

JSON。机器原生，人类可读。
- 推导链每一步都有 SymPy 表达式 → **确定性验算**
- 每一条声张都有 confidence + 正反证据 + 审查记录 → **透明**
- 被证伪的声张不会被删除——和存活的声张一样重要 → **诚实**
- 你的 ORCID 在上面。你的发现永远属于你 → **确权**

---

## 怎么提交

```
1. 用 Polaris 跑完课题 → GATE 7 产出 JSON
2. Fork 本仓库 → 放到 entries/
3. 提 PR → 自动校验 → 合入
```

## 入库标准

**不是所有 JSON 都能进。但门槛不是"AI 写的吗"。**

| 自动检查 | 人工抽查 |
|---------|---------|
| JSON schema 合法 | ≥1 个 confidence ≥ 0.6 的节点 |
| metrics.py ≥ 70% | surviving + killed 都不为空 |
| contributor.github 存在 | 抽查 1 个 DOI 真实 |
| 至少 1 个引用格式有效 | 没有 ORCID → 提醒注册 |

详见 [REVIEW_POLICY.md](REVIEW_POLICY.md)

## 分类

每份 JSON 带三类标签，可从已有选也可自创：
- **领域**：arXiv 分类（cond-mat, hep-th, quant-ph...）
- **矛盾类型**：hidden-assumption / exp-vs-theory / theory-vs-theory...
- **方法标签**：自由填写

详见 [TAXONOMY.md](TAXONOMY.md)

## 链接

- **引擎**：[polaris](https://github.com/val1813/polaris) — 跑课题的 SOP
- **格式**：[validation/schema.md](https://github.com/val1813/polaris/blob/main/validation/schema.md) — JSON 标准
- **链接器**：[knowledge_graph/linker.py](https://github.com/val1813/polaris/blob/main/knowledge_graph/linker.py) — 把分散的 JSON 织成图谱

## 许可

所有条目以 **CC0（公共领域）** 发布。你的 ORCID 永远关联你的发现。

---

<p align="center">
  <sub>「科学不是谁做的——是结果能不能被检验。」</sub>
</p>
