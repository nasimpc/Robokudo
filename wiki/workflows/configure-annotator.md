---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
---

# Configure Annotator

Use this workflow when an annotator needs per-pipeline parameters.

## Steps

1. Inspect the annotator descriptor class and its default `parameters`.
2. In the analysis engine, instantiate the descriptor.
3. Override the relevant `descriptor.parameters` values before creating the annotator.
4. Pass the descriptor to the annotator constructor.
5. For custom annotators, add the same descriptor pattern to the annotator class.

## Source

- [[sources/configure-your-annotator|Configure your Annotator]]
