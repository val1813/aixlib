# Polaris JSON 科学发现格式规范 v1.0

> **不需要 Polaris。不需要任何特定工具。** 把你的科学发现写成这份 JSON，任何 AI 都能帮你生成。

## 一分钟看懂

```json
{
  "project": {
    "id": "MY-001",
    "title": "你的发现一句话",
    "domain": "cond-mat.str-el",
    "contradiction_type": "hidden-assumption",
    "tags": ["renormalization-group"],
    "date": "2026-06-04",
    "contributor": {
      "orcid": "0000-0002-1825-0097",
      "github": "your-username",
      "name": "可选"
    }
  },
  "contradiction": {
    "proposition_A": "现有认知A",
    "proposition_B": "矛盾现象B",
    "why_not_both": "为什么A和B不能同时为真",
    "resolution": "你的发现如何解决了这个矛盾"
  },
  "derivation_chain": [
    {
      "step": 1,
      "description": "推导步骤",
      "formulas": [
        {
          "label": "F1",
          "expression": "m/(n*e**2*tau)",
          "variables": {"m": "electron_mass", "n": "density", "e": "charge", "tau": "scattering_time"},
          "units": "ohm*meter"
        }
      ],
      "assumptions": ["假设1"]
    }
  ],
  "claims": [
    {
      "id": "C1",
      "statement": "核心声张一句话",
      "confidence": 0.75,
      "status": "survived",
      "evidence_for": ["支持证据"],
      "evidence_against": ["反对证据（诚实记录）"]
    }
  ],
  "predictions": [
    {
      "id": "P1",
      "statement": "可检验预言",
      "observable": "可观测量名称",
      "expected_values": {"value": 0.433, "uncertainty": 0.05, "unit": "dimensionless"},
      "measurement_conditions": "测量条件"
    }
  ],
  "validation": {
    "dimension_checks": {"total": 2, "passed": 2, "failed": 0},
    "prior_art_search": {"performed": true, "tool": "paper-search-mcp"}
  },
  "source_files": "指向原始推导文件的路径或URL",
  "lessons": ["如果重来，我会..."],
  "references": [
    {"doi": "10.1103/PhysRevLett.75.1260", "label": "Author Year", "role": "foundation"}
  ]
}
```

## 字段说明

⛔ **derivation_chain 和 validation 是必填项。** 没有推导链和验证数据的 JSON = 只有结论没有过程 = 不可验证 = 退回。

### `id` — 唯一标识符

**格式：`GitHub用户名-编号`**。GitHub 用户名全球唯一，前缀保证不撞。

| 来源 | 格式 | 示例 |
|------|------|------|
| **Polaris 自动生成** | `用户名-LP序号` | `val1813-LP27` |
| **自主研究** | `用户名-领域-序号` | `val1813-CM-001`、`zhangsan-Q-003` |

**为什么必须带用户名：** 两个人各自跑 Polaris，各自产出 `LP27` → 撞了。`val1813-LP27` 和 `zhangsan-LP27` → 永不撞。不用 Polaris 的人也一样——`CM-007` 会撞，`val1813-CM-007` 不会。

**作用：** 被其他 JSON 引用、linker 建立跨课题连接、检索去重。
命名后不可改——这是你在知识网络里的永久坐标。

## 核心规则

1. **derivation_chain 不能为空**：没有推导过程的声张 = 不可验证。至少 1 步推导，至少 1 个带 SymPy 表达式的公式
2. **validation 必须填写**：量纲检查几项通过几项失败？先发检索做了吗？——不是 AI 说的，是验证工具跑的
3. **公式用 SymPy 格式**：`**` 不用 `^`，`exp()` 不用 `e^`，`sin()` 不用 `\sin`
4. **confidence 诚实**：0.3 也是科学。0.95 以上请特别论证
5. **surviving AND killed**：被证伪的声张和被验证的一样重要。两者都要有
6. **lessons 不能为空**：没有完美的研究。至少写一条教训
7. **引用带 DOI**：每条 reference 尽量有 DOI。没有 DOI 的标注 "(no DOI)"
8. **ORCID 确权**：你的发现属于你。免费注册 [orcid.org](https://orcid.org)

## 给 AI 的提示词

**复制下面这段话，发给任何 AI（Claude、ChatGPT、DeepSeek...），它就会按标准格式输出：**

```
请把我的研究发现整理成 Polaris JSON 科学发现格式。

⛔ 必须包含：derivation_chain（推导链+公式）+ validation（验证数据）。没有推导过程的声张不可入库。

格式规范如下：

{
  "project": {"id": "GitHub用户名-编号", "title": "标题", "domain": "领域(见分类表)", "contradiction_type": "矛盾类型(见分类表)", "tags": ["方法标签"], "date": "日期", "contributor": {"orcid": "ORCID", "github": "GitHub用户名", "name": "姓名"}},
  "contradiction": {"proposition_A": "现有认知", "proposition_B": "矛盾现象", "why_not_both": "为何不共存", "resolution": "你的解决"},
  "derivation_chain": [{"step": 1, "description": "...", "formulas": [{"label": "F1", "expression": "SymPy格式公式", "variables": {}, "units": "SI单位"}], "assumptions": ["假设"], "validation": {"dimensions": "PASS或FAIL"}}],
  "validation": {"dimension_checks": {"total": N, "passed": N, "failed": N}, "prior_art_search": {"performed": true, "tool": "使用的工具"}},
  "claims": [{"id": "C1", "statement": "声张", "confidence": 0.75, "status": "survived或killed", "evidence_for": [], "evidence_against": []}],
  "predictions": [{"id": "P1", "statement": "预言", "observable": "可观测量", "expected_values": {"value": 数字, "uncertainty": 数字, "unit": "单位"}, "measurement_conditions": "条件"}],
  "source_files": "原始推导文件路径或URL",
  "lessons": ["教训1"],
  "references": [{"doi": "DOI", "label": "标签", "role": "foundation/support/prior_art/contradiction"}]
}

分类参考：
领域(domain): cond-mat.str-el(强关联) | hep-th(高能理论) | gr-qc(引力宇宙) | quant-ph(量子) | physics.bio-ph(生物物理) | 或自填
矛盾类型(contradiction_type): exp-vs-theory(实验vs理论) | theory-vs-theory(理论vs理论) | hidden-assumption(隐藏假设) | structural-isomorphism(跨学科同构) | no-go-violation(禁止定理突破) | 或自填
方法标签(tags): 自由填写,如 renormalization-group, information-theoretic, monte-carlo, symmetry-breaking...

公式规范：用 ** 不用 ^ | 用 exp() 不用 e^ | 用 sin() 不用 \sin
confidence: 0.0~1.0，诚实标注。0.3也是科学。
status: survived(存活) 或 killed(被证伪)——两种都要有。

我的研究发现是：
[这里粘贴你的研究发现、推导过程、公式、数据...]
```

## 快速开始

**路径 A：用 Polaris 自动生成**
```
按科研SOP开展科研 → 跑完 3 轮 → GATE 7 自动产出 JSON
```

**路径 B：让 AI 帮你整理（不需要 Polaris）**
1. 复制上面的提示词
2. 把你的研究发现贴进去
3. AI 输出标准 JSON
4. 检查一下 → 提 PR 到本仓库

**两份文件就够了：** 这份 `FORMAT.md` + [`demo_entry.json`](demo_entry.json)。把这两个给任何 AI，说"按这个格式整理我的发现"。
