---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[wiki/sources/create-your-own-annotator|Create your own Annotator]]"
---

# RoboKudo

RoboKudo is a robot perception framework organized around reusable behavior-tree components. Its tutorials describe a flow where users run an existing [[wiki/concepts/pipelines|pipeline]], create their own package, add [[wiki/concepts/annotators|annotators]], configure them, and expose perception tasks through the [[wiki/concepts/query-interface|Query Interface]].

## Core Pieces

- [[wiki/concepts/pipelines|Pipelines]] define perception behavior as analysis engines.
- [[wiki/concepts/annotators|Annotators]] perform local perception work and add annotations.
- [[wiki/concepts/common-analysis-structure|Common Analysis Structure]] is the shared data container used by annotators.
- [[wiki/concepts/package-structure|Package Structure]] separates custom perception code from RoboKudo core code.
