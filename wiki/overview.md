---
type: overview
status: active
created: 2026-06-28
updated: 2026-07-01
sources:
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[sources/reading-data-from-a-database|Reading data from a Database]]"
  - "[[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# RoboKudo Overview

RoboKudo is presented in these tutorials as a modular perception framework where [[concepts/pipelines|Pipelines]] are analysis engines built from behavior-tree nodes. The central reusable units are [[concepts/annotators|Annotators]], which read from and write to the [[concepts/common-analysis-structure|Common Analysis Structure]].

The tutorial path is connected through [[tutorials/robokudo-tutorial-overview|RoboKudo Tutorial overview]]. It starts with running a demo pipeline, then moves into creating a separate RoboKudo package, adding a custom annotator, configuring annotator parameters, exposing perception work through the [[concepts/query-interface|Query Interface]], using MongoDB-backed storage, and running in Docker. The upstream navigation also references a WSL tutorial, but that source is absent from the current corpus, so it is not represented as a wiki node.

## Mental Model

- A RoboKudo project organizes perception behavior as ROS packages with descriptor modules and annotator modules.
- An analysis engine is the named pipeline entrypoint passed to RoboKudo at startup.
- Annotators are behavior-tree nodes; their `update` methods do the main work.
- Annotator descriptors hold metadata and parameters, allowing per-pipeline configuration.
- Query support is action-oriented: receive a task, place it into the CAS, let annotators react, and return a result, failure, or feedback.
- Advanced query handling is ROS 2-specific in this corpus and adds validation, live feedback, cancellation, and preemption behavior.
- Database storage records perception inputs for faster development and replay.
- Docker support covers GPU-enabled container execution for ROS 2 workflows.

## Reading Path

1. [[workflows/run-demo-pipeline|Run Demo Pipeline]]
2. [[workflows/create-package|Create Package]]
3. [[workflows/create-annotator|Create Annotator]]
4. [[workflows/configure-annotator|Configure Annotator]]
5. [[workflows/run-query-workflow|Run Query Workflow]]
6. [[workflows/use-database-storage|Use Database Storage]]
7. [[workflows/run-in-docker|Run in Docker]]

## Corpus Gaps

- Installation pages are referenced by the tutorials but are not part of the current converted corpus.
- The wiki has not been validated against a live RoboKudo checkout.
- Source mirror pages preserve all converted source content; synthesized pages intentionally stay shorter.
