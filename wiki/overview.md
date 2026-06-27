---
type: overview
status: active
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[wiki/sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[wiki/sources/configure-your-annotator|Configure your Annotator]]"
  - "[[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[wiki/sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[wiki/sources/reading-data-from-a-database|Reading data from a Database]]"
  - "[[wiki/sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# RoboKudo Overview

RoboKudo is presented in these tutorials as a modular perception framework where [[wiki/concepts/pipelines|Pipelines]] are analysis engines built from behavior-tree nodes. The central reusable units are [[wiki/concepts/annotators|Annotators]], which read from and write to the [[wiki/concepts/common-analysis-structure|Common Analysis Structure]].

The tutorial path starts with running a demo pipeline, then moves into creating a separate RoboKudo package, adding a custom annotator, configuring annotator parameters, and exposing perception work through the [[wiki/concepts/query-interface|Query Interface]].

## Current Mental Model

- A RoboKudo project organizes perception behavior as ROS packages with descriptor modules and annotator modules.
- An analysis engine is the named pipeline entrypoint passed to RoboKudo at startup.
- Annotators are behavior-tree nodes; their `update` methods do the main work.
- Annotator descriptors hold metadata and parameters, allowing per-pipeline configuration.
- Query support is action-oriented: receive a task, place it into the CAS, let annotators react, and return a result or failure.
- Advanced ROS 2 query handling adds validation, live feedback, and preemption behavior.
- Database storage is used to record perception inputs for faster development and replay.
- Docker support targets GPU-enabled environments and requires display forwarding for visualization.

## Reading Path

1. [[wiki/workflows/run-demo-pipeline|Run Demo Pipeline]]
2. [[wiki/workflows/create-package|Create Package]]
3. [[wiki/workflows/create-annotator|Create Annotator]]
4. [[wiki/workflows/configure-annotator|Configure Annotator]]
5. [[wiki/workflows/run-query-workflow|Run Query Workflow]]
6. [[wiki/workflows/use-database-storage|Use Database Storage]]
7. [[wiki/workflows/run-in-docker|Run in Docker]]

## Open Gaps

- Installation pages are referenced by the tutorials but are not part of the current raw corpus.
- The API reference pages linked from the Sphinx navigation are not part of the current raw corpus.
- The wiki has not yet been validated against a live RoboKudo checkout.
