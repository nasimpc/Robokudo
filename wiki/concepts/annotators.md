---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[wiki/sources/configure-your-annotator|Configure your Annotator]]"
---

# Annotators

Annotators are RoboKudo's reusable perception components. They inherit from `BaseAnnotator`, participate in the behavior tree, and normally implement their main logic in `update`.

## Responsibilities

- Read data from the [[wiki/concepts/common-analysis-structure|Common Analysis Structure]].
- Add or modify annotations for downstream annotators.
- Return behavior-tree status values.
- Expose configuration through descriptors when parameters should be pipeline-specific.

## Practical Constraint

The tutorial warns that behavior-tree ticks should remain short. Long-running computer-vision work should use `ThreadedAnnotator`.

## Related

- [[wiki/workflows/create-annotator|Create Annotator]]
- [[wiki/concepts/annotator-configuration|Annotator Configuration]]
- [[wiki/reference/code-entrypoints|Code Entrypoints]]
