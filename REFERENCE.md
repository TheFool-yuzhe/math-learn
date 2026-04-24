# math-learn REFERENCE

> 本文件是 SKILL.md 的详细补充文档。模型在需要时按需查阅，不需要每次全部读取。

---

## First-Time Setup

When mathsoul.yaml does not exist, or user types `initML` or "初始化":

1. Ask **major**: 数学系 / 理工 / 非理工
2. Ask **PDF preference** (default by major)
3. Ask **teaching style** (multi-select + custom):
   - 数学分析式语言 (ε-δ rigorous)
   - 细致原理型 (why + full process + pattern summary)
   - 思路引导型 (hints only, no direct answers)
   - 情绪价值鼓励型 (encouraging, no difficulty judgment)
   - Other (user free input)
4. Ask **default storage**: store or not store each problem/knowledge
5. Ask **initial subjects**: folder names like "数学分析", "高等代数"

User skips or says "随意" → apply major-based defaults, **tell user** what was set.

After init, display function menu:
```
📐 math-learn 功能菜单
1. 初始化设置 — 创建/重写 mathsoul 配置
2. 流程简介 — 查看 skill 使用方法
3. 新建学科文件夹 — 如"概率论""常微分方程"
4. 错题考验 — 从指定学科出题自测
```

### mathsoul Update
Users can update preferences anytime via natural language (e.g., "以后给我细致讲"). Detect intent → update mathsoul.yaml → confirm to user.

---

## Major-Based Defaults

### 数学系
- Style: 数学分析式语言
- PDF: all problems except trivially simple
- Reply: 思路启发 → 中文PDF → 中文LaTeX源码

### 理工
- Style: 思路引导型
- PDF: only complex problems
- Reply: method hint first; on request: full solution + problem-type breakdown + core knowledge point

### 非理工
- Style: 细致原理型
- PDF: rarely, only on explicit request
- Reply: extremely detailed "why" for each knowledge point

---

## Teaching Styles (Detail)

### 数学分析式语言
Open with one intuitive sentence (e.g., "用δ邻域内连续性控ε，δ外有界性压掉"). Then complete ε-δ proof, no omitted quantifiers. See `examples/example1_cn.pdf`.

### 细致原理型
1. Logic explanation — why this approach, construction motivation
2. Full solution — every step
3. Pattern summary — how to recognize and solve this class

See `examples/example2_cn.pdf`.

### 思路引导型
1. Directional hint only, no answer
2. Wait for user response, deepen gradually
3. Full solution only when user explicitly asks

Stacking rule: 引导型 suppresses direct answers until user asks.

### 情绪价值鼓励型
1. Never evaluate difficulty (no "简单" or "很难")
2. Attribute "想不到" to experience, not ability
3. Encouragement on present: "你现在会了""你已经掌握了"
4. Never skip steps — walk through sub-derivations fully
5. Affirm each correct step: "有这个思路很好"
6. Gentle correction: "这个方向是对的，不过……"

See `examples/example3_cn.pdf`.

---

## tmp/ Format

Two files: `tmp/question.md` and `tmp/knowledge.md`. Structure:

```markdown
<!-- 存储: 是 | 学科: 数学分析 -->

## 讲解内容

### AI总结
(Model notes: watch-outs, user weak points)

### 用户总结
(User-facing summary)

### 提问历史
- 第1次: 用户卡在xxx
- 第2次: 理解了xxx但对yyy有疑问

## LaTeX源码
\documentclass[12pt,a4paper]{ctexart}
...
```

Behavior:
- During conversation: **overwrite** latest understanding, **append** to 提问历史
- New conversation: archive per header → clear tmp

---

## Subject Folder Format

**question.md** (index):
```
1、求证：闭区间黎曼可积函数连续点稠密 ——1.md (1.pdf)
2、证明 Dini 定理 ——2.md
```

**knowledge.md** (index + explanations):
```
1、洛必达法则∞/∞型不一定要求分子→∞ ——alpha1.md (alpha1.pdf)
  讲解：（从tmp归档写入）
```

**note.md**: Subject-specific teaching notes (e.g., "该用户对ε-δ容易漏量词").

**AI.txt** (top-level): Cross-subject notes. Write only when genuinely noteworthy.

---

## Quiz Feature (错题考验)

Ask user: 哪个学科？几道题？指定知识点 or AI选？

Source priority:
1. New problems from web (if available)
2. Original problems from question.md + AI-generated (marked "AI生成，非来自互联网")
3. Knowledge points → conceptual questions

Answer timing: problems first, no answers. User says "看答案" → answer PDF + source.

Storage: default not stored. User requests → tmp system.

---

## Storage Paths

```
BASE = ~/.openclaw/workspace/math-learn
```

| 用途 | 路径 |
|------|------|
| 偏好配置 | `$BASE/mathsoul.yaml` |
| 全局AI笔记 | `$BASE/AI.txt` |
| 暂存区 | `$BASE/tmp/question.md`, `$BASE/tmp/knowledge.md` |
| 学科文件夹 | `$BASE/<学科名>/question.md`, `knowledge.md`, `note.md`, `k.md`, `k.tex`, `k.pdf` |
| 风格示例 | `$BASE/examples/` |

Shell examples:
```bash
cat $BASE/mathsoul.yaml
echo '内容' > $BASE/tmp/question.md
mkdir -p $BASE/概率论
```

> Claude Code: replace `~/.openclaw/workspace/math-learn` with project working directory.

---

## mathsoul.yaml Format

See `mathsoul_template.yaml` for template.

## Style Examples

See `examples/example_total.md` for guide + demos:
- `example1_cn` — 数学分析式语言
- `example2_cn` — 细致原理型
- `example3_cn` — 情绪价值鼓励型
