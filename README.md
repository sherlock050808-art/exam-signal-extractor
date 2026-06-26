# Open Book Exam Assistant（开卷闭卷考试助手）

> 版本：v2.0  
> 核心升级：从“怎么做复习资料”重新定义为“**如何从海量教学信息中提取对考试最有预测价值的信号**”。

这是一套可复用的考试复习方法论仓库，帮助你把课堂录音、课件、随堂练习等零散信息，整理成一张高命中率的“七层考试地图”，再针对开卷或闭卷考试生成可直接上考场的复习资料。

---

## 项目简介

**这不是题库**，也不 memorizes 具体题目。它沉淀的是一套“信号 > 内容”的考试准备工作流：

- **信号源**：课堂录音 / 录屏转录文本、老师划重点、课件标题、往年题。
- **输出物**：七层考试地图 + 名词解释清单 + 简答题 + 综合分析题 + 索引。
- **适用对象**：想系统化备考、愿意花 2–4 小时前置整理、希望把复习精力投到“最可能考”的内容上的同学。

> **关键认知**：录音决定考试范围，PPT/课件填充知识内容。不要把二者等权处理。

---

## 核心方法论

### 1. 从课堂录音中提取考试信号

老师关于考试的话，预测价值往往远高于知识本身。本方法把原始转录文本经过 6 步处理：

```text
原始转录文本
  ├── 步骤1 硬过滤：删除元数据、语气词、课堂动作等确定性噪声
  ├── 步骤2 话题切分：按主题切成 15–20 段
  ├── 步骤3 意图单元合并+粗分类：把连续句子合并为“意图单元”
  ├── 步骤4 精细提取：提取知识点、题型、确定性、答题要点
  ├── 步骤5 课件对照验证：把课件标题级内容升入考点
  └── 步骤6 输出考试地图：按七层结构重组
```

详细步骤见 [`docs/methodology/extracting-exam-signals-from-recordings.md`](docs/methodology/extracting-exam-signals-from-recordings.md)。

### 2. 七层考试地图

同一套七层框架同时服务开卷和闭卷考试，差异只在于各层的**覆盖深度**和**投入权重**。

| 层次 | 含义 |
|------|------|
| 🟢 必考层 | 老师明确强调、极大概率会考的考点 |
| 🟡 高概率层 | 多次暗示、结构性重点、往年高频的考点 |
| 🟠 可能层 | 课件标题级概念、老师随口提到但不确定的内容 |
| 🔴 排除层 | 明确不考的内容，节省复习精力 |
| ⚡ 陷阱区 | 易混淆概念、常见错误、区分方式 |
| 🔗 融合区 | 跨章节组合，可能出综合分析题的考点对 |
| ❓ 待确认 | 信息不足，需要考前确认或人工判定的条目 |

模板见 [`templates/exam-map-template.md`](templates/exam-map-template.md)。

### 3. 开卷 vs 闭卷策略

两种考试形式共用同一张地图，但资料形态不同：

| 维度 | 开卷考试 | 闭卷考试 |
|------|----------|----------|
| 资料厚度 | 厚，但必须可检索 | 薄，按七层分层清晰 |
| 记忆强度 | 以识别和定位为主 | 以默写和调用为主 |
| 前置页 | 考试地图 + 快速索引 | 题型分布（推荐）或目录 |
| 必考层 | 完整答案 + 索引定位 + 快速照抄 | 完整记忆 + 能默写 |
| 高概率层 | 完整答案 + 索引定位 | 重点记忆采分点 + 能展开 |

完整策略见：
- [`docs/methodology/open-book-strategy.md`](docs/methodology/open-book-strategy.md)
- [`docs/methodology/closed-book-strategy.md`](docs/methodology/closed-book-strategy.md)

---

## 使用流程

### 方式一：让 AI 读取 Skill 文档（推荐）

把 [`docs/SKILL.md`](docs/SKILL.md) 提供给 Kimi / Claude 等支持长上下文的助手，然后说：

> “按这个帮我准备《XXX》考试，这是课堂录音转录文本和课件。”

AI 会自动确认考试形式、执行六步工作流、生成考试地图和复习资料。

### 方式二：手动按工作流执行

1. 准备材料：课堂录音转录文本、课件 PDF/PPT、往年题（如有）。
2. 阅读 [`docs/methodology/extracting-exam-signals-from-recordings.md`](docs/methodology/extracting-exam-signals-from-recordings.md)。
3. 按六步工作流提取信号，填写 [`templates/exam-map-template.md`](templates/exam-map-template.md)。
4. 根据开卷/闭卷策略，套用 [`templates/`](templates/) 下的模板生成考场资料。
5. 考前使用 [`checklists/pre-exam-checklist.md`](checklists/pre-exam-checklist.md) 检查。
6. 考后填写 [`checklists/post-exam-checklist.md`](checklists/post-exam-checklist.md)，沉淀为 few-shot 样本。

### 方式三：只看模板快速上手

如果你只需要一个格式参考，直接打开 [`templates/`](templates/) 和 [`examples/`](examples/)，照葫芦画瓢即可。

---

## 目录说明

```text
open-book-exam-assistant/
├── README.md                                    # 本文件
├── LICENSE                                      # MIT 许可证
├── .gitignore                                   # Git 忽略规则
├── docs/
│   ├── SKILL.md                                 # 可直接给 AI 读取的 Skill 调用文档
│   └── methodology/
│       ├── extracting-exam-signals-from-recordings.md  # v2.0 核心方法论
│       ├── information-distillation-sop.md             # v1.0 历史版本 SOP
│       ├── open-book-strategy.md                       # 开卷策略
│       ├── closed-book-strategy.md                     # 闭卷策略
│       └── post-exam-review-checklist.md               # 考后复盘清单（参考版）
├── examples/
│   └── consumer-goods-intelligent-equipment/
│       ├── exam-map-example.md                  # 七层考试地图示例
│       └── post-exam-review.md                  # 真实考后复盘
├── templates/
│   ├── exam-map-template.md                     # 七层考试地图空白模板
│   ├── term-definition-template.md              # 名词解释清单模板
│   ├── short-answer-template.md                 # 简答题模板
│   └── comprehensive-analysis-template.md       # 综合分析题模板
└── checklists/
    ├── pre-exam-checklist.md                    # 考前检查清单
    └── post-exam-checklist.md                   # 考后复盘清单
```

---

## 贡献方式

欢迎贡献你的考试地图、复盘、模板改进或翻译！

1. **Fork 本仓库**。
2. 在 `examples/` 下新增你的学科案例（建议用英文目录名，如 `advanced-mathematics/`）。
3. 如果某种题型或老师的出题模式反复出现，更新 `templates/` 或 `checklists/`。
4. 提交 Pull Request，说明你的改进点和验证结果（例如“本次考试命中了 8/10 个考点”）。

贡献时请遵守：
- 不要上传具体考题原文，避免版权问题。
- 分享的是**方法、模板、结构化的复盘**，而不是原始试卷。
- 保持中文内容，文件路径建议使用英文小写 + 连字符。

---

## 许可证声明

本项目采用 [MIT License](LICENSE) 开源。你可以自由使用、修改、分发，但请保留版权声明。

---

## 快速开始

如果你是第一次使用，建议按下面顺序阅读：

1. [`docs/methodology/extracting-exam-signals-from-recordings.md`](docs/methodology/extracting-exam-signals-from-recordings.md)
2. [`examples/consumer-goods-intelligent-equipment/post-exam-review.md`](examples/consumer-goods-intelligent-equipment/post-exam-review.md)
3. [`templates/exam-map-template.md`](templates/exam-map-template.md)
4. [`checklists/pre-exam-checklist.md`](checklists/pre-exam-checklist.md)

祝你考试顺利，命中率拉满！
