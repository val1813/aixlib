<p align="center">
  <img src="https://img.shields.io/badge/Registry-v1.0-2563eb?style=for-the-badge&logo=starship&logoColor=white">
  <img src="https://img.shields.io/badge/Entries-0-22c55e?style=for-the-badge&logo=googleresearch&logoColor=white">
  <img src="https://img.shields.io/badge/License-CC0-lightgrey?style=for-the-badge">
</p>

# Polaris Registry — 人类知识图书馆

> **科学进步不应该有门槛。**
> 不需要博士学位。不需要学会写论文。不需要考虑"AI 检测率"。
> 你只需要有"这里好像有问题"的直觉——然后把你认为对的、有用的发现，交到这里。

---

## 为什么建这个图书馆

读研、读博、发论文、申基金、过同行评审——这是过去两百年的科学之路。它筛选出了很多好东西，**也筛掉了很多人**。

一个文科生，对量子力学有一个直觉——"这个假设好像从来没被检验过"。他没有实验室，没有导师，不会写 LaTeX。但他用 AI 探索了三轮，找到了一个真正的逻辑矛盾。这个东西有价值吗？

**我们认为有。**

不是因为他写得像 Nature。是因为——矛盾是真实的，推导是透明的，每一条声张都标注了确信度，被推翻的部分没有被偷偷删掉，引用的论文都有 DOI。

这就是我们建这个图书馆的原因：

> **让每一个人——无论文理、无论学历——都能在 AI 的辅助下推进科学进步。**

你不用写"Dear Editor"。不用考虑叙事结构。不用纠结 AI 检测率。不用把 AI 的痕迹藏起来。

**你只需要交一份 JSON。** 里面是你认为对的、有促进的发现。机器来验机械的部分，人来审语义的部分。能过就入库。过不了就改。很简单。

---

## 不是去 AI 化。是换一个格式。

现在的学术圈在内耗什么？

> AI 写论文 → 另一个 AI 查 AI 痕迹 → 降到了 8%！→ 投稿 → 审稿人："这里写得不像人" → 再改

把算力花在骗检测器上。把创造力花在"装人"上。

**我们不玩这个游戏。我们换格式。**

JSON。机器原生，人类可读。
- 推导链每一步都有 SymPy 表达式 → **确定性验算**
- 每一条声张都有 confidence + 正反证据 → **透明**
- 被证伪的声张不会被删除——和存活的声张一样重要 → **诚实**
- 你的 ORCID 在上面。你的发现永远属于你 → **确权**

---

## 快速开始

**两份文件就够了：** [`FORMAT.md`](FORMAT.md) + [`demo_entry.json`](demo_entry.json)

### 路径 A：用 Polaris 自动生成

```
按科研SOP开展科研 → 跑完 → 自动产出 JSON → 提 PR
```

### 路径 B：让任何 AI 帮你生成（零依赖）

```
1. 打开 FORMAT.md → 复制里面的"给 AI 的提示词"
2. 粘贴你的研究发现
3. AI 输出标准 JSON
4. 放到 entries/ → 提 PR
```

**不需要装任何东西。** 只要你有研究发现（哪怕是在别的 AI 工具上探索出来的），把 FORMAT.md + demo_entry.json 扔给 AI，说"按这个格式整理我的发现"。

## 怎么提交

```
1. 准备好你的 JSON
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
  <sub>「科学不是谁做的。是你发现了什么，别人能不能复现。」</sub>
</p>
