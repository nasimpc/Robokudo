---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
---

# Pipelines

RoboKudo pipelines are called analysis engines in the tutorials. They are behavior-tree definitions located under `descriptors/analysis_engines` inside a RoboKudo package.

## Notes

- The analysis engine name is passed at startup as `_ae=...`.
- The built-in demo pipeline is started with `_ae=demo`.
- A custom copied pipeline can be renamed to `my_demo` and started with `_ae=my_demo _ros_pkg=rk_tutorial`.
- Pipelines compose annotators and other behavior-tree nodes.

## Related

- [[wiki/workflows/run-demo-pipeline|Run Demo Pipeline]]
- [[wiki/workflows/create-package|Create Package]]
- [[wiki/concepts/annotators|Annotators]]
