# PDF Extraction Workflows

## Single PDF To Literature Matrix Row

Read only the provided PDF. Do not use outside information unless the user explicitly requests verification.

Output one row using the schema in `matrix_schema.md`.

Rules:

- If a field is not reported, write `not_reported`.
- If a field is unclear, write `needs_manual_check`.
- Use only allowed values for controlled fields.
- Keep each cell concise enough for Excel.
- Add evidence or uncertainty in `notes`.
- For preprints, set `publication_status = preprint`.
- For low-food-relevance but high-method-value papers, use `priority = A*` and add a transferability caveat.

## Deep Reading Note

Use this structure for A-priority papers.

1. Basic information
   - Title
   - Year
   - Journal
   - DOI
   - Paper type
   - Research object

2. Why this paper matters
   - Main research question
   - Main contribution
   - Why it is relevant to the current research project or matrix goal

3. Carbohydrate-related information
   - Carbohydrate type
   - Food relevance
   - Structural problem addressed
   - Structural features discussed

4. Traditional characterization methods
   - HPGPC / SEC-MALS
   - Monosaccharide composition
   - Methylation analysis
   - FT-IR / Raman / NIR
   - NMR
   - LC-MS/MS
   - Other methods

5. AI-related information
   - AI or computational method used
   - Model/tool name
   - Input data
   - Output
   - Dataset
   - Evaluation method
   - Main result

6. Structure elucidation relevance
   - Structure prediction, representation, spectral interpretation, or characterization
   - Structure information addressed
   - Applicability to food polysaccharides, oligosaccharides, glycans, or glycoproteomics

7. Limitations
   - Data limitations
   - Method limitations
   - Applicability limitations to food or bioactive polysaccharides

8. How to use this paper
   - Suitable research section
   - Suitable table or figure
   - Priority
   - Transferability caveat if needed
   - One-sentence takeaway

## AI Input-Output Extraction

For AI/computational papers, extract:

| Field | Required content |
|---|---|
| `model_or_tool` | Name of model/tool if reported |
| `input_data` | MS/MS spectra, NMR shifts, graph, descriptors, database, etc. |
| `output` | Structure, composition, linkage, chemical shift, candidate ranking, class, etc. |
| `ai_method` | RF, SVM, CNN, GNN, Transformer, deep learning, rule based |
| `carbohydrate_type` | Glycan, oligosaccharide, food polysaccharide, etc. |
| `structure_problem` | Specific structure problem |
| `main_contribution` | Main contribution |
| `limitation` | Key limitation |
| `transferability_to_food_carbohydrates` | high, medium, low with explanation |
| `evidence_from_pdf` | Short evidence phrase; do not overquote |

## Extraction, Purification, And Process Optimization Extraction

For extraction, purification, fractionation, degradation, modification, or process optimization papers, extract:

| Field |
|---|
| extraction_or_process_method |
| raw_material |
| polysaccharide_fraction |
| optimization_variables |
| yield_or_purity |
| structural_evidence |
| functional_endpoint |
| ai_or_statistical_method |
| process_structure_function_link |
| key_limitation |

Do not assign high priority to yield-only optimization unless the paper also provides structural evidence, functional evidence, or modelable process variables.

## Table 1 Extraction

For conventional methods, extract:

| Field |
|---|
| method |
| structural_information_obtained |
| data_type |
| advantages |
| limitations |
| ai_usable_features |
| example_from_this_paper |

Only include methods actually mentioned in the PDF.

## Table 3 Extraction

For AI-assisted MS/NMR papers, extract:

| Field |
|---|
| paper_id |
| title |
| year |
| carbohydrate_type |
| analytical_platform |
| data_type |
| ai_method |
| model_or_tool |
| input |
| output |
| structure_information_predicted |
| dataset |
| validation_method |
| main_contribution |
| key_limitation |
| food_carbohydrate_relevance |

If the paper is not an AI-assisted MS/NMR/spectroscopy study, state why it should not be included in Table 3.

## Structure-Function Extraction

For papers linking polysaccharides to gut microbiota, immune activity, SCFA, metabolites, inflammation, or intestinal barrier markers, extract:

| Field |
|---|
| polysaccharide_source |
| structural_descriptors |
| biological_model |
| microbiota_or_metabolite_endpoint |
| immune_or_barrier_endpoint |
| statistical_or_ai_method |
| structure_function_claim |
| evidence_strength |
| causality_limitation |
| validation_needed |

Separate correlation from causality. Do not treat microbiota shifts or inflammatory marker changes as proof of mechanism unless the paper provides direct mechanistic validation.
