<p align="center">
  <img src="https://img.shields.io/badge/Registry-v1.0-2563eb?style=for-the-badge&logo=starship&logoColor=white">
  <img src="https://img.shields.io/badge/Entries-0-22c55e?style=for-the-badge&logo=googleresearch&logoColor=white">
  <img src="https://img.shields.io/badge/License-CC0-lightgrey?style=for-the-badge">
</p>

# Polaris Registry — 社区知识库

> **每一份 JSON 是一个发现。不写论文，交 JSON。**
> 引擎 → [polaris](https://github.com/val1813/polaris) | 图书馆 → 本仓库

## 怎么提交

```
1. 用 Polaris 跑完课题 → GATE 7 产出 JSON
2. Fork 本仓库
3. 把 JSON 放到 entries/
4. 提 PR
5. 自动校验通过 → 人工审核 → 合入
```

## 入库标准

| 自动检查 | 人工抽查 |
|---------|---------|
| JSON schema 合法 | ≥1 个 confidence ≥ 0.6 的节点 |
| metrics.py ≥ 70% | surviving + killed 都不为空 |
| contributor.github 存在 | 抽查 1 个 DOI 真实 |
| 至少 1 个引用格式有效 | 没有 ORCID → 提醒注册 |

详见 [REVIEW_POLICY.md](REVIEW_POLICY.md)

## 分类

每份 JSON 带三类标签：
- **领域**：arXiv 分类（cond-mat, hep-th, quant-ph...）
- **矛盾类型**：hidden-assumption / exp-vs-theory / theory-vs-theory / ...
- **方法标签**：自由填写

详见 [TAXONOMY.md](TAXONOMY.md)

## 浏览

- [entries/](entries/) — 所有条目
- [index.json](index.json) — 可搜索索引
- 网站: `polaris-registry.github.io`（GitHub Pages，待建）

## 许可

所有条目以 CC0（公共领域）发布。你的 ORCID 永远关联你的发现。
