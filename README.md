# Food Carb Review Assistant

OpenClaw skill for assisting the review:

**Artificial intelligence-assisted structural elucidation of food carbohydrates: advances, challenges, and future perspectives**

The skill helps parse user-provided PDFs into a literature matrix, classify papers into review sections, extract AI input-output relationships, assess preprints and transferability, synthesize multiple papers, draft section-level prose, prepare table/figure materials, and quality-check extraction results.

## Install

Copy this folder into one of OpenClaw's skill locations, for example:

```text
<workspace>/.agents/skills/food-carb-review-assistant
```

or:

```text
~/.openclaw/skills/food-carb-review-assistant
```

## Typical Use

Ask OpenClaw:

```text
Use the food-carb-review-assistant skill to parse this PDF into my literature matrix.
```

or:

```text
Use the food-carb-review-assistant skill to extract the AI input-output workflow from this PDF.
```

For multi-paper synthesis:

```text
Use the food-carb-review-assistant skill to compare these matrix rows and synthesize the method evolution.
```

For section writing:

```text
Use the food-carb-review-assistant skill to draft the AI-assisted MS/MS section from these A-priority matrix rows.
```

## Notes

The skill is designed to avoid unsupported claims. Missing information should be marked as `not_reported`, and uncertain information should be marked as `needs_manual_check`.

The skill supports `A*` priority for papers with high method value but low or indirect food relevance, such as preprints or medical glycomics papers that require domain adaptation before use in food carbohydrate research.
