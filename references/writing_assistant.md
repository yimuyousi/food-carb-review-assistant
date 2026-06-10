# Writing Assistant

Use this reference when the user asks to draft review sections or paragraphs from matrix rows, reading notes, or extracted evidence.

## Purpose

Turn structured extraction into review prose while preserving critical thinking.

Do not write generic summaries. The output should connect papers, identify trends, and highlight limitations.

## Inputs

The user may provide:

- All A/A* priority rows for one section.
- A comparison table.
- Deep reading notes.
- Table materials.

Use only the provided content unless the user asks for additional verification or searching.

## Section Draft Output

For a section draft, output:

1. **Section thesis**
   - One sentence stating the main argument of the section.

2. **Paragraph draft**
   - 1-3 paragraphs depending on user request.
   - Use citation placeholders such as `[P001]`, `[P002]`.
   - Do not fabricate author names, years, or citations not present in the input.

3. **Critical evaluation**
   - 3-5 bullet points on limitations, uncertainty, transferability, or unresolved challenges.

4. **Transition sentence**
   - One sentence linking this section to the next section.

5. **Suggested figure/table link**
   - State whether the section should refer to Table 1, Table 2, Table 3, Table 4, or a figure.

## Writing Style

Use an academic review style:

- Precise.
- Critical.
- Not promotional.
- Avoid overclaiming.
- Distinguish "enables", "supports", "suggests", and "demonstrates".

## Common Section Logic

### AI-ready data and representation

Recommended logic:

1. AI needs standardized inputs.
2. Food polysaccharides often lack fully defined structures.
3. Tabular descriptors suit intact heterogeneous polysaccharides.
4. Graph/sequence representations suit defined glycans or oligosaccharides.
5. Databases and controlled formats are prerequisites for transferable models.

### AI-assisted MS/MS

Recommended logic:

1. MS/MS provides fragment evidence.
2. AI can improve annotation, candidate ranking, and structure prediction.
3. Most models are trained on glycans/glycoproteomics data.
4. Food polysaccharides require controlled depolymerization into oligosaccharides.
5. Transferability requires food-derived benchmark datasets.

### AI-assisted NMR and spectroscopy

Recommended logic:

1. NMR provides linkage and residue-environment evidence.
2. AI can support chemical shift prediction and peak assignment.
3. FT-IR/Raman/NIR models often classify fingerprints rather than solve structures.
4. Human-in-the-loop interpretation remains necessary.
5. Multimodal MS/NMR integration is a promising direction.

### Applications in food carbohydrates

Recommended logic:

1. Different food carbohydrates have different structural bottlenecks.
2. Beta-glucans, pectins, arabinoxylans, inulin/FOS, starch-derived oligosaccharides, mushroom polysaccharides, and algal polysaccharides require different descriptors.
3. AI opportunities depend on available structural evidence and datasets.
4. Structure-function claims require experimental validation.

## A* Citation Handling

For A* papers:

- Cite as methodologically important but not directly food-specific.
- Include a caveat in the prose.
- Do not use A* papers as direct evidence for food carbohydrate performance.

Example sentence pattern:

`Although [Pxxx] was developed in a non-food glycan context, it provides a transferable strategy for [specific task]; however, applying this approach to food carbohydrates will require domain-specific annotated spectra and validation on food-derived oligosaccharides.`

## Prohibited Writing

Do not write:

- "AI completely solves carbohydrate structural elucidation."
- "This method can be directly applied to all food polysaccharides" unless the provided paper proves it.
- "More research is needed" as a standalone limitation.
- Unsupported performance comparisons.
