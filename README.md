# math-learn

## 数学.skill

---

> *"你们搞大模型的简直是码圣，你们已经解放码农兄弟了，还要解放数学兄弟，统计兄弟，数学学得好的兄弟，数学学得不好的兄弟，最后解放自己、解放理工兄弟、解放全人类！"*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://github.com/TheFool-yuzhe/math-learn)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://github.com/TheFool-yuzhe/math-learn)

你问数学大神题，就留下一句"不难注意到"的轻描淡写？

你的教授讲完了定理，微微一笑："证明留作习题"？

你翻开习题集，第一行写着"显然"，然后就没有然后了？

## **我們的教育確有問題！**

将"我们发现"的习题变为温暖的讲解，加入赛博自学。**學的好的，獎勵一塊華為手錶！**

给 AI 你的题目（拍照、打字、粘贴 LaTeX）加上你的困惑，生成一个**真正帮你学会的讲解** —— 用你听得懂的语言，按你需要的节奏，记住你踩过的坑，下次不让你再踩。

---

## 讲题风格

- **数学分析式语言** 📐 ：直觉式的思路总结，加上从头到尾的 ε-δ 语言严谨证明——把你当希腊人！
- **细致原理型** 🔍 ：抽丝剥茧式的"为什么要这么做" + 完整解题 + 题型通用套路总结，把每道题拆到你再也没有疑问为止
- **思路引导型** 🧭 ：苏格拉底附体——不告诉你答案，一步步把你引到真相面前，让你自己说出那个"啊我懂了"
- **情绪价值鼓励型** 🌟 ：很好你已经完全掌握了！你真的很棒！（不是在嘲讽你，是认真的）

风格可以叠加，详见 [`examples/example_total.md`](examples/example_total.md)。

---

## 文件结构

### Skill 自身文件

```
math-learn/
├── README.md                    # 你正在看的这个
├── LICENSE                      # MIT License
├── SKILL.md                     # 核心规则（极简，模型每次必读）
├── REFERENCE.md                 # 详细规范（初始化、风格、存储格式等，按需查阅）
├── mathsoul_template.yaml       # 偏好配置模板
├── math_learn_design_doc.tex    # 全流程设计文档（中文 LaTeX 源码）
└── examples/                    # 风格示例
    ├── example_total.md         # 四种风格总领说明 + 用户自定义扩展区
    ├── example1_cn.tex          # 数学分析式语言（中文 LaTeX 源码）
    ├── example1_cn.pdf          # 数学分析式语言（编译后 PDF）
    ├── example2_cn.tex          # 细致原理型（中文 LaTeX 源码）
    ├── example2_cn.pdf          # 细致原理型（编译后 PDF）
    ├── example3_cn.tex          # 情绪价值鼓励型（中文 LaTeX 源码）
    └── example3_cn.pdf          # 情绪价值鼓励型（编译后 PDF）
```

### 运行时生成的工作区

```
~/.openclaw/workspace/math-learn/    # 运行时根目录
├── mathsoul.yaml         # 你的偏好配置（初始化时生成）
├── AI.txt                # 全局讲题笔记（AI 自我提示，跨学科共享）
├── tmp/                  # 暂存区（栈结构，对话中覆写，新对话时归档）
│   ├── question.md       # 当前题目暂存
│   └── knowledge.md      # 当前知识点暂存
├── 数学分析/              # 学科文件夹（示例）
│   ├── question.md       # 题目索引汇总
│   ├── knowledge.md      # 知识点索引 + 讲解
│   ├── note.md           # 本学科局部教学注意点
│   ├── 1.md, 2.md, ...   # 单题详细讲解
│   ├── 1.tex, 2.tex, ... # 对应中文 LaTeX 源码
│   └── 1.pdf, 2.pdf, ... # 编译后 PDF（如有）
├── 高等代数/
│   └── ...
└── 概率论/
    └── ...
```

---

## 快速开始

输入 `initML`，按提示完成：
1. 选择专业（数学系 / 理工 / 非理工）
2. 选择讲题风格（可多选、可叠加）
3. 设置默认存储和学科

设置完成后直接丢题目即可。

## 功能

| 功能 | 触发方式 |
|------|---------|
| 初始化 / 重设偏好 | `initML` 或 "初始化" |
| 问题讲解 | 直接提问 |
| 修改偏好 | 自然语言，如 "以后给我引导式" |
| 新建学科 | "新建一个概率论文件夹" |
| 错题考验 | "出几道数学分析的题" |
| 查看流程 | "流程简介" |

---

## PDF 说明

默认编译**中文 PDF**（ctexart + XeLaTeX），同时附中文 LaTeX 源码。

你也可以把自己编译好的 PDF 交给模型，模型按命名规则自动归档。

---

## 兼容性

本 skill 设计兼容以下环境运行：

| 环境 | 支持程度 |
|------|---------|
| **OpenClaw**（推荐） | 完整功能，本地持久化，iPad / 手机远程调用 |
| **Codex / Claude Code** | 完整功能，本地终端环境 |
| **网页版大模型** | 仅讲题风格偏好 |

网页版大模型（Claude.ai / DeepSeek 等）限制：模型环境中文 LaTeX 编译不稳定，改为英文 PDF + 中文源码；memory 有限，无法文件持久化。

---

### **好了，花點時間去挑戰數學有趣的難題，不再討論這件事情了！**
