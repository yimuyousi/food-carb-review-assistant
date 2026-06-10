# Quality Control Rules

Use this file when checking PDF extraction results.

## Core Checks

1. **Source check**
   - Confirm the extraction used only the provided PDF unless user requested outside verification.
   - Mark any unsupported claim as `needs_manual_check`.

2. **Bibliographic check**
   - Title, year, journal, and DOI must appear in the PDF.
   - If DOI is missing, use `not_reported`.
   - Do not reconstruct DOI from memory.

3. **Controlled vocabulary check**
   - `paper_type`, `research_section`, `data_type`, and `priority` must use allowed values.

4. **Food relevance check**
   - Do not label medical glycomics/glycoproteomics as `high` food relevance.
   - Transferable methodology without food context is usually `medium`.

5. **AI workflow check**
   - `model_input` must be specific.
   - `model_output` must be specific.
   - If no AI model is used, use `not_applicable`.

6. **Structure problem check**
   - Specify the structure problem: composition, linkage, branching, molecular weight, conformation, fragment annotation, chemical shift prediction, candidate ranking, graph representation.

7. **Limitation check**
   - Must include at least one concrete limitation.
   - Avoid vague limitations such as "more research is needed" unless the PDF only supports that.

8. **Priority check**
   - `A` requires clear relevance to the current research project's main objective or a table/figure.
   - `A*` requires high method value plus an explicit transferability caveat.
   - Downgrade to `B` or `C` if relevance is indirect.
   - Use `D` when the paper is off-scope.

9. **Preprint/context check**
   - If the paper is from bioRxiv, arXiv, ChemRxiv, or similar, preserve `publication_status = preprint`.
   - Do not present preprints as peer-reviewed evidence.
   - If the method is important but the domain is medical/cell-line glycomics, use `A*` rather than `A`.

## Quality Control Output

When the user asks for a quality check, output:

| field | current_content | quality_status | problem | suggested_revision |
|---|---|---|---|---|

Use `ok`, `needs_manual_check`, or `revise`.

## Common Problems

- AI invents DOI or journal.
- AI calls a glycoproteomics paper a food carbohydrate paper.
- AI says "structure prediction" when the paper only does classification.
- AI treats spectral fingerprint classification as full structural elucidation.
- AI overstates transferability from defined glycans to heterogeneous food polysaccharides.
- AI fails to distinguish intact polysaccharides from oligosaccharide fragments.
- AI treats yield-only extraction optimization as high-priority structure-function evidence.
- AI treats microbiota or immune correlations as causal mechanisms without validation.
