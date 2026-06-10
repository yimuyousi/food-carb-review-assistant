# Polysaccharide Research Assistant 中文说明

这是一个用于 OpenClaw 的通用多糖研究助理型 skill。它不绑定任何具体论文题目或项目名称，对外呈现为“多糖研究、文献矩阵、结构解析、结构-功能关系和 AI 辅助研究”的通用工作流。

## 这个 skill 能做什么

它主要帮助你完成：

- 读取你提供的 PDF。
- 提取论文基本信息。
- 判断论文属于哪个多糖研究主题。
- 生成文献矩阵的一行。
- 提取 AI 模型的输入、输出、数据集、贡献和局限。
- 判断文献适合进入正文、表格、图或讨论部分。
- 给文献分 `A`、`A*`、`B`、`C`、`D` 优先级。
- 对 preprint、医学糖组学或低食品相关性文献进行上下文判断。
- 对多篇论文做横向比较和方法演进总结。
- 根据矩阵行生成英文或中文段落草稿。
- 标记需要人工核查的信息。
- 防止 AI 编造 DOI、模型名称、数据集或结论。

## 适用研究方向

这个 skill 适合处理以下方向的文献：

- 食品碳水化合物和生物活性多糖。
- β-葡聚糖、果胶、阿拉伯木聚糖、菊粉/FOS、抗性淀粉、食用菌多糖、海藻多糖、药食同源多糖等。
- 多糖提取、纯化、分级、结构表征和工艺优化。
- HPGPC/SEC-MALS、单糖组成、甲基化、FT-IR、Raman、NIR、NMR、LC-MS/MS 等表征方法。
- AI 辅助 MS/MS 糖结构分析。
- AI 辅助 NMR 化学位移预测和谱图解析。
- 糖结构数据库、结构表示、图神经网络、语言模型和多模态学习。
- 多糖结构-肠道菌群关系。
- 多糖结构-免疫活性关系。
- 多糖结构-SCFA/代谢物关系。
- 多糖结构-功能关系的可解释机器学习研究。

## 不适合直接高优先级纳入的情况

以下文献需要降级或谨慎处理：

- 纯医学糖组学，且没有可迁移的结构分析方法。
- 只研究糖蛋白疾病标志物，不能迁移到食品或生物活性多糖研究。
- 只有提取工艺优化，没有结构、功能或模型证据。
- 只有抗氧化活性，没有结构证据。
- AI 应用泛泛而谈，但没有清楚的模型输入和输出。

## 文件结构

```text
polysaccharide-research-assistant/
├─ SKILL.md
├─ README.md
├─ README.zh-CN.md
└─ references/
   ├─ research_scope.md
   ├─ matrix_schema.md
   ├─ pdf_extraction_prompts.md
   ├─ multi_paper_synthesis.md
   ├─ writing_assistant.md
   └─ quality_control_rules.md
```

## 核心文件说明

`SKILL.md`

OpenClaw 识别和调用 skill 的主文件，包含触发描述、工作流和基本规则。

`references/research_scope.md`

定义通用研究范围、纳入标准、排除标准和研究主题分类。

`references/matrix_schema.md`

定义文献矩阵字段，例如：

- `paper_id`
- `title`
- `year`
- `journal`
- `doi`
- `research_section`
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

定义 PDF 解析工作流，包括单篇 PDF 提取、深度精读、AI 输入-输出关系提取、表格素材提取和结构-功能信息提取。

`references/multi_paper_synthesis.md`

用于多篇论文对比，帮助你比较模型输入、输出、数据集、优点、局限和方法演进。

`references/writing_assistant.md`

用于把矩阵行转化为段落草稿、批判性讨论、过渡句和图表引用建议。

`references/quality_control_rules.md`

用于检查是否存在编造、误判、过度推断或需要人工核查的字段。

## 推荐安装位置

把整个文件夹复制到 OpenClaw 可以识别的 skills 路径，例如：

```text
<workspace>/.agents/skills/polysaccharide-research-assistant
```

或者：

```text
~/.openclaw/skills/polysaccharide-research-assistant
```

## 典型使用方式

给 OpenClaw 一个 PDF 后，可以这样说：

```text
请使用 polysaccharide-research-assistant skill，把这个 PDF 解析成我的文献矩阵一行。
```

如果是重要文献：

```text
请使用 polysaccharide-research-assistant skill，对这篇 PDF 做 A 类文献深度精读。
```

如果是 AI 方法文献：

```text
请使用 polysaccharide-research-assistant skill，提取这篇论文中 AI 模型的输入、输出、方法、数据集、贡献和局限。
```

如果要比较多篇论文：

```text
请使用 polysaccharide-research-assistant skill，对这些文献矩阵行做多论文综合，比较它们的方法输入、输出、数据集、局限和可迁移性。
```

如果要写作辅助：

```text
请使用 polysaccharide-research-assistant skill，根据这些 A-priority 文献矩阵行，起草这一节的英文学术段落，并给出批判性评价。
```

如果要质控：

```text
请使用 polysaccharide-research-assistant skill，检查刚才的文献矩阵提取结果是否有编造、误判或需要人工核查的字段。
```

## 文献优先级规则

`A`：必须精读，可能进入核心正文、表格或图。

`A*`：食品或多糖对象相关性较低，或属于 preprint，但方法价值很高。可以用于方法学讨论，但必须写清楚迁移到食品/生物活性多糖研究还需要领域数据集、结构标注和实验验证。

`B`：重要背景文献，可能引用。

`C`：补充文献，暂时保留。

`D`：不适合当前研究目标，建议剔除。

## 重要原则

这个 skill 不是替你判断最终结论，而是帮你做：

```text
PDF -> 信息提取 -> 文献矩阵 -> 主题归类 -> 多论文综合 -> 图表素材 -> 写作草稿 -> 质控
```

最终是否引用、是否列为 A 类、是否进入正文，仍然需要你人工判断。

## 当前版本建议

第一版先用于半自动流程：

1. 你自己检索并下载 PDF。
2. 你把 PDF 给 OpenClaw。
3. OpenClaw 使用这个 skill 解析。
4. 你把结果复制到 Excel 文献矩阵。
5. 你人工核查。

等处理 20-30 篇文献后，再考虑加入自动化脚本，例如批量读取 PDF、自动写入 Excel、检查缺失字段、生成表格初稿和汇总报告。
