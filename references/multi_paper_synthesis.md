# Multi-Paper Synthesis

Use this reference when the user provides multiple matrix rows, reading notes, or extracted paper summaries and asks for comparison, synthesis, method evolution, or section-level logic.

## Purpose

Move beyond single-paper extraction. Help the user answer:

- How do these papers differ?
- What is the method evolution?
- Which papers are foundational, incremental, or application-oriented?
- Which papers belong in the same table or paragraph?
- Which limitations are shared across papers?
- Which papers are transferable to food carbohydrates, and which require domain adaptation?
- Which extraction/process variables are connected to structure or function?
- Which structure-function claims are only correlative, and which have stronger mechanistic support?

## Required Inputs

Accept any of:

- Literature matrix rows.
- Deep reading notes.
- AI input-output extraction tables.
- User-provided paper list.

If key fields are missing, mark them as `needs_manual_check`.

## Comparison Table Output

For method comparison, output:

| paper_id | title_short | year | publication_status | carbohydrate_context | food_relevance | method_or_model | input_data | output | key_strength | key_limitation | transferability_to_food_carbohydrates | priority |
|---|---|---:|---|---|---|---|---|---|---|---|---|---|

`publication_status` values:

- `peer_reviewed`
- `preprint`
- `database/tool_page`
- `needs_manual_check`

## Method Evolution Output

After the table, provide:

1. **Chronological logic**: how the methods evolved over time.
2. **Technical logic**: what changed in data type, model architecture, representation, or output.
3. **Scope logic**: from general glycan/glycoproteomics to food carbohydrate transferability.
4. **Remaining gap**: what still prevents direct use on heterogeneous food polysaccharides.

Keep the synthesis critical. Do not list papers one by one without connecting them.

## A* Priority Rule

Use `A*` when a paper is highly methodologically important but not directly food-carbohydrate focused.

Typical examples:

- Medical glycan language models.
- Glycoproteomics MS/MS models.
- Preprint AI models for glycan representation.
- Cell-line glycan datasets.

Required caveat:

**This method is transferable in principle, but application to food carbohydrates requires domain-specific datasets, structural annotation standards, and validation on food polysaccharide or oligosaccharide samples.**

## Synthesis Prompts

When comparing AI MS/MS papers, focus on:

- Spectrum input format.
- Output structure granularity.
- Candidate ranking versus direct prediction.
- Dataset size and annotation quality.
- Whether linkage/branching is addressed.
- Applicability to oligosaccharides from food polysaccharides.

When comparing AI NMR papers, focus on:

- Chemical shift prediction versus structure ranking.
- 1D versus 2D NMR information.
- Data source and structure diversity.
- Whether the method handles branched carbohydrates.
- Whether it supports human-in-the-loop assignment.

When comparing representation/model papers, focus on:

- Sequence, graph, language model, or descriptor representation.
- Whether the model needs fully defined structures.
- Whether heterogeneous polysaccharides can be represented.
- Whether food carbohydrate datasets exist.

When comparing extraction, purification, or process optimization papers, focus on:

- Raw material and polysaccharide fraction.
- Extraction or purification variables.
- Whether the paper links process variables to molecular weight, monosaccharide composition, linkage, conformation, purity, or bioactivity.
- Whether optimization is yield-only or structure/function-informed.
- Whether the design supports model building beyond response surface fitting.

When comparing structure-function, microbiota, or immune papers, focus on:

- Structural descriptors used as explanatory variables.
- Biological endpoints, including microbiota, SCFA/metabolites, cytokines, immune cells, inflammation, and barrier markers.
- Whether the study separates correlation from causality.
- Whether the model is interpretable and experimentally validated.
- Whether confounders such as source, purity, dose, molecular weight distribution, and batch variation are controlled.

## Output Discipline

- Use only the supplied rows or notes unless the user requests web verification.
- Do not invent performance metrics.
- If metrics are incomparable, say so explicitly.
- If preprint status is present, preserve it.
