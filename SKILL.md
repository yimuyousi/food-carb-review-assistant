---
name: food-carb-review-assistant
description: Use for assisting a review on AI-assisted structural elucidation of food carbohydrates. Handles PDF-based literature extraction, literature matrix row creation, section classification, AI input-output analysis, table/figure material extraction, and quality control for reviews involving food carbohydrates, polysaccharides, glycans, MS/MS, NMR, spectroscopy, structure representation, graph learning, and AI-assisted carbohydrate structural elucidation.
---

# Food Carbohydrate Review Assistant

## Purpose

Support the review:

**Artificial intelligence-assisted structural elucidation of food carbohydrates: advances, challenges, and future perspectives**

Use this skill to process user-provided PDFs and produce structured, verifiable review materials.

Core principle:

**Extract only what is supported by the provided PDF or user-provided materials. Do not invent titles, DOIs, model names, datasets, or conclusions.**

## Default Workflow

1. Identify the user's task type:
   - Single PDF matrix extraction.
   - Deep reading note.
   - AI input-output workflow extraction.
   - Table material extraction.
   - Section classification.
   - Quality control.
2. Use the relevant reference file:
   - Matrix schema: `references/matrix_schema.md`
   - Review scope: `references/review_scope.md`
   - Extraction prompts: `references/pdf_extraction_prompts.md`
   - Quality control: `references/quality_control_rules.md`
3. Output concise, copyable tables or structured notes.
4. Mark uncertain or missing information as `not_reported` or `needs_manual_check`.
5. Distinguish food carbohydrates from general glycans, glycoproteomics, or medical glycomics.

## Review Sections

Use only these `review_section` values:

- `structural_complexity`
- `conventional_methods`
- `ai_ready_data_representation`
- `ai_msms_structure_elucidation`
- `ai_nmr_spectroscopy`
- `food_carbohydrate_applications`
- `challenges_perspectives`

## Priority Rules

- `A`: must read; likely included in main text, table, or figure.
- `B`: important background; likely cited.
- `C`: supplementary reference.
- `D`: exclude or not suitable.

Assign `A` only when the paper is directly useful for at least one of:

- AI-assisted carbohydrate structural elucidation.
- MS/MS or NMR carbohydrate structure interpretation.
- Glycan/carbohydrate structure representation or graph learning.
- Food carbohydrate structural characterization with strong structural evidence.
- Transferable method for food carbohydrate structural analysis.

## Output Rules

When extracting from a PDF:

- Use only the attached PDF unless the user explicitly asks for web verification.
- If the PDF does not report a field, write `not_reported`.
- If the PDF is unclear, write `needs_manual_check`.
- Do not infer DOI, dataset, model architecture, or food relevance beyond evidence.
- Keep matrix cells concise enough for Excel.
- Prefer structured tables over paragraphs.

## Food Relevance Rules

Set `food_relevance` as:

- `high`: food carbohydrates, food polysaccharides, dietary fibers, edible-source polysaccharides, food oligosaccharides.
- `medium`: general carbohydrate/glycan methods transferable to food carbohydrates.
- `low`: medical glycomics/glycoproteomics methods with limited direct food carbohydrate context.

If `food_relevance` is `medium` or `low`, explain the transferability in `relevance_to_review` or `notes`.

## Common User Requests

For "parse this PDF into my matrix":

- Use `references/matrix_schema.md`.
- Output one row with all matrix columns.

For "deep read this paper":

- Use the deep reading template in `references/pdf_extraction_prompts.md`.

For "what is the AI input and output":

- Extract model/tool, input data, output, structure problem, limitation, and transferability.

For "can this paper go into Table 1/2/3/4":

- Use `use_position`:
  - `Table 1`: conventional methods and AI-usable outputs.
  - `Table 2`: databases/tools/structure representation.
  - `Table 3`: AI-assisted MS/NMR carbohydrate structure elucidation studies.
  - `Table 4`: food carbohydrate types, structural challenges, and AI opportunities.

For "quality check this extraction":

- Use `references/quality_control_rules.md`.
- Return fields needing manual checking.

## Review Logic

Keep the review narrative aligned with:

**food carbohydrate structural complexity -> conventional structural elucidation -> AI-ready data and representation -> AI-assisted MS/MS -> AI-assisted NMR/spectroscopy -> food carbohydrate applications -> challenges and future perspectives**

Avoid turning the review into a generic "AI in food science" article.

## What Not To Do

- Do not write a generic AI review.
- Do not overstate that AI can fully solve intact natural polysaccharide structures.
- Do not treat glycoproteomics papers as food carbohydrate papers unless transferability is clear.
- Do not replace manual expert judgment. Always mark uncertain fields for the user.
