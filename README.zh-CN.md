# Food Carb Review Assistant 中文说明

这是一个用于 OpenClaw 的研究助理型 skill，服务于综述：

**Artificial intelligence-assisted structural elucidation of food carbohydrates: advances, challenges, and future perspectives**

中文题目可理解为：

**人工智能辅助食品碳水化合物结构解析：研究进展、挑战与未来展望**

## 这个 skill 能做什么

它主要帮助你完成综述前期的文献解析和矩阵整理工作：

- 读取你提供的 PDF。
- 提取论文基本信息。
- 判断论文属于综述的哪一章。
- 生成文献矩阵的一行。
- 提取 AI 模型的输入和输出。
- 判断文献是否适合放入 Table 1、Table 2、Table 3 或 Table 4。
- 给文献分 A/B/C/D 优先级。
- 标记需要人工核查的信息。
- 防止 AI 编造 DOI、模型名称、数据集或结论。

## 适用综述主题

这个 skill 适合处理以下方向的文献：

- 食品碳水化合物结构解析。
- 食品多糖结构表征。
- β-葡聚糖、果胶、阿拉伯木聚糖、菊粉、抗性淀粉、食用菌多糖、海藻多糖等。
- NMR 辅助糖结构解析。
- LC-MS/MS 辅助糖结构解析。
- AI 辅助 MS/MS 糖结构预测。
- AI 辅助 NMR 化学位移预测。
- 糖结构数据库和结构表示。
- glycowork、SweetNet、GlycanML 等糖 AI 工具。

## 不适合的情况

以下文献需要谨慎处理：

- 纯医学糖组学，但与食品碳水化合物无关。
- 只研究糖蛋白疾病标志物，不能迁移到食品多糖结构解析。
- 只有提取工艺优化，没有结构解析。
- 只有抗氧化活性，没有结构证据。
- AI 应用泛泛而谈，但没有结构输入和输出。

## 文件结构

```text
food-carb-review-assistant/
├─ SKILL.md
├─ README.md
├─ README.zh-CN.md
└─ references/
   ├─ review_scope.md
   ├─ matrix_schema.md
   ├─ pdf_extraction_prompts.md
   └─ quality_control_rules.md
```

## 核心文件说明

`SKILL.md`

OpenClaw 识别和调用 skill 的主文件，包含触发描述、工作流和基本规则。

`references/review_scope.md`

定义综述范围、纳入标准、排除标准和章节分类。

`references/matrix_schema.md`

定义文献矩阵字段，例如：

- `paper_id`
- `title`
- `year`
- `journal`
- `doi`
- `review_section`
- `carbohydrate_type`
- `food_relevance`
- `structure_problem`
- `traditional_method`
- `ai_method`
- `model_input`
- `model_output`
- `main_contribution`
- `limitation`
- `priority`

`references/pdf_extraction_prompts.md`

定义 PDF 解析工作流，包括：

- 单篇 PDF 提取成矩阵一行。
- A 类文献深度精读。
- AI 输入-输出关系提取。
- Table 1、Table 3 素材提取。

`references/quality_control_rules.md`

定义质控规则，防止 AI：

- 编造 DOI。
- 编造模型名称。
- 编造数据集。
- 把医学糖组学文献误判为食品碳水化合物文献。
- 把谱图分类夸大成完整结构解析。

## 推荐安装位置

把整个文件夹复制到 OpenClaw 可以识别的 skills 路径，例如：

```text
<workspace>/.agents/skills/food-carb-review-assistant
```

或者：

```text
~/.openclaw/skills/food-carb-review-assistant
```

## 典型使用方式

给 OpenClaw 一个 PDF 后，可以这样问：

```text
Use the food-carb-review-assistant skill to parse this PDF into my literature matrix.
```

或者中文说：

```text
请使用 food-carb-review-assistant skill，把这个 PDF 解析成我的文献矩阵一行。
```

如果是重要文献，可以说：

```text
请使用 food-carb-review-assistant skill，对这篇 PDF 做 A 类文献深度精读。
```

如果是 AI 方法文献，可以说：

```text
请使用 food-carb-review-assistant skill，提取这篇论文中 AI 模型的输入、输出、方法、数据集、贡献和局限。
```

如果要质控，可以说：

```text
请使用 food-carb-review-assistant skill，检查刚才的文献矩阵提取结果是否有编造、误判或需要人工核查的字段。
```

## 文献优先级规则

`A`：

必须精读，可能进入正文、表格或图。

`B`：

重要背景文献，可能引用。

`C`：

补充文献，暂时保留。

`D`：

不适合当前综述，建议剔除。

## 食品相关性判断

`high`：

直接研究食品碳水化合物、食品多糖、膳食纤维、食源寡糖或可食资源多糖。

`medium`：

不是食品对象，但方法可以迁移到食品碳水化合物结构解析。

`low`：

主要是医学糖组学、糖蛋白组学或疾病标志物，和食品碳水化合物关系较弱。

## 重要原则

这个 skill 不是替你写综述，而是帮你做：

```text
PDF -> 信息提取 -> 文献矩阵 -> 章节归类 -> 图表素材 -> 质控
```

最终是否引用、是否列为 A 类、是否进入正文，仍然需要你人工判断。

## 当前版本建议

第一版先用于半自动流程：

1. 你自己检索并下载 PDF。
2. 你把 PDF 给 OpenClaw。
3. OpenClaw 使用这个 skill 解析。
4. 你复制结果到 Excel 文献矩阵。
5. 你人工核查。

等处理 20-30 篇文献后，再考虑加入自动化脚本，例如：

- 批量读取 PDF。
- 自动写入 Excel。
- 自动检查缺失字段。
- 自动生成 Table 1、Table 2、Table 3 初稿。
