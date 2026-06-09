# Food Carb Review Assistant

OpenClaw skill for assisting the review:

**Artificial intelligence-assisted structural elucidation of food carbohydrates: advances, challenges, and future perspectives**

The skill helps parse user-provided PDFs into a literature matrix, classify papers into review sections, extract AI input-output relationships, prepare table/figure materials, and quality-check extraction results.

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

## Notes

The skill is designed to avoid unsupported claims. Missing information should be marked as `not_reported`, and uncertain information should be marked as `needs_manual_check`.
