# Polysaccharide Research Assistant

OpenClaw skill for general polysaccharide research workflows.

It uses neutral project language such as "current research project", "research section", and "literature matrix", so it can be reused across different polysaccharide research topics.

## What It Does

- Parse user-provided PDFs into a literature matrix.
- Classify papers into general polysaccharide research sections.
- Extract AI model inputs, outputs, datasets, contributions, and limitations.
- Assess preprints, medical glycomics papers, and cross-domain transferability.
- Compare multiple papers and synthesize method evolution.
- Draft section-level academic prose from supplied matrix rows.
- Prepare table and figure materials.
- Quality-check extraction results and mark unsupported claims.
- Optionally use a local private project context for project-specific writing without publishing that context.

## Research Coverage

The skill is designed for work involving:

- Food carbohydrates and bioactive polysaccharides.
- Beta-glucans, pectins, arabinoxylans, inulin/FOS, resistant starch, mushroom polysaccharides, algal polysaccharides, and medicinal-food homologous polysaccharides.
- Polysaccharide extraction, purification, structural characterization, and process optimization.
- MS/MS, NMR, FT-IR, Raman, NIR, chromatography, methylation analysis, and multimodal spectroscopy.
- Glycan databases, graph/sequence representations, and carbohydrate AI methods.
- Gut microbiota, SCFA/metabolites, immune activity, intestinal barrier markers, and interpretable structure-function modeling.

## Install

Copy this folder into one of OpenClaw's skill locations, for example:

```text
<workspace>/.agents/skills/polysaccharide-research-assistant
```

or:

```text
~/.openclaw/skills/polysaccharide-research-assistant
```

If the GitHub repository folder has an older name, you can still use the skill as long as `SKILL.md` is present. For public clarity, the recommended folder name is `polysaccharide-research-assistant`.

## Typical Use

```text
Use the polysaccharide-research-assistant skill to parse this PDF into my literature matrix.
```

```text
Use the polysaccharide-research-assistant skill to extract the AI input-output workflow from this PDF.
```

```text
Use the polysaccharide-research-assistant skill to compare these matrix rows and synthesize the method evolution.
```

```text
Use the polysaccharide-research-assistant skill to draft a section from these A-priority matrix rows.
```

## Notes

Missing information should be marked as `not_reported`. Unclear information should be marked as `needs_manual_check`.

Use `A*` priority for papers with high methodological value but indirect relevance, such as preprints, medical glycomics papers, or general glycan AI methods that require domain adaptation before use in food or bioactive polysaccharide research.

For project-specific writing, copy `references/project_context_template.md` to `.private/project_context.local.md` and fill it locally. The `.private/` folder is ignored by Git and should not be pushed to GitHub.
