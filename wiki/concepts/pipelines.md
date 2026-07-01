---
type: concept
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
---

# Pipelines

A RoboKudo pipeline is an analysis engine: a Python descriptor that builds a behavior tree from annotators and helper behaviors. The demo pipeline starts with `pipeline_init()`, reads sensor data, preprocesses images, crops point clouds, finds planes, extracts clusters, and can add annotators such as `ClusterColorAnnotator`.

At runtime the analysis engine name is passed as `_ae`, for example `demo`, `storage`, `demo_from_storage`, `my_demo`, or `query_complex`.

## Related

- [[workflows/run-demo-pipeline|Run Demo Pipeline]]
- [[reference/code-entrypoints|Code Entrypoints]]
