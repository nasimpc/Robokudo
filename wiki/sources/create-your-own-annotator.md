---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/create_your_own_annotator.html
source_title: Create your own Annotator
source_type: html
ingested: 2026-06-27
sources: []
---

# Create your own Annotator

This tutorial builds a minimal custom annotator that checks for a pointcloud in the CAS and reports its size.

## Key Points

- [[wiki/concepts/annotators|Annotators]] are RoboKudo's modular perception components.
- Every annotator inherits from `BaseAnnotator`, itself a `py_trees` behavior.
- The main runtime method is `update`.
- The tutorial warns that behavior-tree ticks should be short; longer computer-vision work should use `ThreadedAnnotator`.
- Annotators access shared data through the [[wiki/concepts/common-analysis-structure|Common Analysis Structure]].
- The new annotator is integrated by importing it into an analysis engine and inserting it into the pipeline.

## Connected Pages

- [[wiki/workflows/create-annotator|Create Annotator]]
- [[wiki/concepts/annotators|Annotators]]
- [[wiki/concepts/common-analysis-structure|Common Analysis Structure]]
- [[wiki/reference/code-entrypoints|Code Entrypoints]]
