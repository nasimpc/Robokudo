---
type: overview
status: active
created: 2026-06-27
updated: 2026-06-27
sources: []
---

# RoboKudo Wiki Index

Start here before answering questions about this vault.

## Overview

- [[wiki/overview|RoboKudo Overview]] - top-level synthesis of the current RoboKudo tutorial corpus.
- [[wiki/log|RoboKudo Wiki Log]] - append-only timeline of ingests, queries, and lint passes.

## Sources

- [[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]] - starts the demo analysis engine, plays test data, and explains the visualizers.
- [[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]] - creates an `rk_tutorial` package and registers a custom analysis engine.
- [[wiki/sources/create-your-own-annotator|Create your own Annotator]] - builds a minimal annotator and inserts it into a pipeline.
- [[wiki/sources/configure-your-annotator|Configure your Annotator]] - explains descriptor-based annotator parameters.
- [[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]] - introduces the Query Interface, query annotator, results, failures, and feedback.
- [[wiki/sources/advanced-query-handling|Advanced Query Handling]] - covers ROS 2 query validation, feedback, cancellation, and preemption in behavior trees.
- [[wiki/sources/reading-data-from-a-database|Reading data from a Database]] - stores and replays perception data with MongoDB-backed storage.
- [[wiki/sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]] - builds and runs RoboKudo in an NVIDIA Docker container.

## Concepts

- [[wiki/concepts/robokudo|RoboKudo]] - framework-level mental model.
- [[wiki/concepts/pipelines|Pipelines]] - analysis engines as behavior-tree perception pipelines.
- [[wiki/concepts/annotators|Annotators]] - reusable behavior nodes that read and write perception annotations.
- [[wiki/concepts/annotator-configuration|Annotator Configuration]] - descriptors and parameter overrides.
- [[wiki/concepts/common-analysis-structure|Common Analysis Structure]] - shared CAS data model used by annotators.
- [[wiki/concepts/query-interface|Query Interface]] - action-based task interface for perception queries.
- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]] - validation, feedback, cancellation, and preemption.
- [[wiki/concepts/database-storage|Database Storage]] - MongoDB-backed recording and replay.
- [[wiki/concepts/docker-usage|Docker Usage]] - GPU container workflow and display forwarding.
- [[wiki/concepts/package-structure|Package Structure]] - ROS package layout for RoboKudo extensions.

## Workflows

- [[wiki/workflows/run-demo-pipeline|Run Demo Pipeline]] - start RoboKudo and play sample data.
- [[wiki/workflows/create-package|Create Package]] - create and verify a custom RoboKudo package.
- [[wiki/workflows/create-annotator|Create Annotator]] - add a simple custom annotator.
- [[wiki/workflows/configure-annotator|Configure Annotator]] - add and override annotator parameters.
- [[wiki/workflows/run-query-workflow|Run Query Workflow]] - wire query receiving, interpretation, and result delivery.
- [[wiki/workflows/use-database-storage|Use Database Storage]] - record and replay sensor scenes through MongoDB.
- [[wiki/workflows/run-in-docker|Run in Docker]] - build and run the RoboKudo container.

## Reference

- [[wiki/reference/commands|Commands]] - ROS 1, ROS 2, Docker, and MongoDB command snippets from the tutorials.
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]] - compatibility and command differences.
- [[wiki/reference/code-entrypoints|Code Entrypoints]] - important modules, files, and APIs mentioned by the sources.

## Questions

- No saved query answers yet.
