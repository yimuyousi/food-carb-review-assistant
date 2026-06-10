# Literature Matrix Schema

Use exactly these columns for `literature_matrix`.

| Column | Meaning | Notes |
|---|---|---|
| `paper_id` | User's paper ID | Example: `P001`; infer from file name if given, otherwise `needs_manual_check` |
| `title` | Paper title | From PDF only |
| `year` | Publication year | From PDF only |
| `journal` | Journal or source | From PDF only |
| `doi` | DOI | Use `not_reported` if absent |
| `paper_type` | Type of paper | `review`, `original`, `method`, `database`, `tool` |
| `publication_status` | Publication status | `peer_reviewed`, `preprint`, `database/tool_page`, `needs_manual_check` |
| `research_section` | Best research topic/section | Use controlled vocabulary |
| `carbohydrate_type` | Main carbohydrate type | Examples: beta_glucan, pectin, glycan, oligosaccharide, general |
| `food_relevance` | Food relevance level | `high`, `medium`, `low` |
| `structure_problem` | Structural problem addressed | Be specific |
| `traditional_method` | Traditional method used/discussed | Example: NMR; LC-MS/MS; methylation; FT-IR |
| `ai_method` | AI/computational method | Example: GNN; CNN; deep_learning; rule_based; none |
| `data_type` | Data used | Use controlled vocabulary |
| `model_input` | Input to AI/model/workflow | Use `not_applicable` if no AI |
| `model_output` | Output of AI/model/workflow | Use `not_applicable` if no AI |
| `main_contribution` | Main contribution | One concise phrase or sentence |
| `limitation` | Key limitation | One concise phrase or sentence |
| `relevance_to_project` | Why this paper matters | Connect to the current research project or matrix goal |
| `transferability_caveat` | Caveat for non-food or low-relevance methods | Required for `A*` |
| `use_position` | Where to use it | main_text, background, Table 1/2/3/4, Figure 1-6, discussion |
| `priority` | A/B/C/D | Follow priority rules |
| `notes` | Extra notes | Include uncertainty flags |

## Controlled Vocabulary

`paper_type`:
- `review`
- `original`
- `method`
- `database`
- `tool`
- `preprint`

`publication_status`:
- `peer_reviewed`
- `preprint`
- `database/tool_page`
- `needs_manual_check`

`research_section`:
- `structural_complexity`
- `conventional_methods`
- `extraction_purification_optimization`
- `ai_ready_data_representation`
- `ai_msms_structure_analysis`
- `ai_nmr_spectroscopy`
- `food_carbohydrate_applications`
- `structure_function_microbiota_immunity`
- `challenges_perspectives`

`data_type`:
- `MSMS_spectrum`
- `NMR_shift`
- `FTIR_spectrum`
- `Raman_spectrum`
- `NIR_spectrum`
- `tabular_descriptor`
- `graph`
- `database`
- `not_applicable`

`priority`:
- `A*`
- `A`
- `B`
- `C`
- `D`

Use `A*` for high-method-value papers with low or indirect food relevance. Always include `transferability_caveat`.

## Table Mapping

`Table 1`: Conventional methods for polysaccharide structural characterization and AI-usable outputs.

`Table 2`: Databases, descriptors, and tools for carbohydrate structure representation.

`Table 3`: AI-assisted MS/NMR/spectroscopy carbohydrate structure analysis studies.

`Table 4`: Polysaccharide types, structural/function challenges, and AI opportunities.
