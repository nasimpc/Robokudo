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

# RoboKudo Wiki Index

Start here before answering questions about this vault. The pages in `wiki/sources/` are full-content mirrors copied from `raw/`; they are not summaries and must stay byte-for-byte identical to the source corpus.

## Overview

- [[overview|RoboKudo Overview]] - top-level synthesis of the current tutorial corpus.
- [[tutorials/robokudo-tutorial-overview|RoboKudo Tutorial overview]] - tutorial sequence node connected to the captured source mirrors.
- [[log|RoboKudo Wiki Log]] - append-only timeline of regeneration and checks.

## Tutorial Node

- [[tutorials/robokudo-tutorial-overview|RoboKudo Tutorial overview]] - connects all captured tutorials listed by the upstream navigation.

Earlier upstream navigation referenced a `Using RoboKudo within WSL` tutorial, but no matching markdown source is present in the current `raw/` corpus, so no wiki node is created for it.

## Source Mirrors

- [[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]] - full mirror of `raw/running-a-pipeline-in-robokudo.md`.
- [[sources/create-your-own-robokudo-package|Create your own RoboKudo package]] - full mirror of `raw/create-your-own-robokudo-package.md`.
- [[sources/create-your-own-annotator|Create your own Annotator]] - full mirror of `raw/create-your-own-annotator.md`.
- [[sources/configure-your-annotator|Configure your Annotator]] - full mirror of `raw/configure-your-annotator.md`.
- [[sources/query-handling-in-robokudo|Query handling in RoboKudo]] - full mirror of `raw/query-handling-in-robokudo.md`.
- [[sources/advanced-query-handling|Advanced Query Handling]] - full mirror of `raw/advanced-query-handling.md`.
- [[sources/reading-data-from-a-database|Reading data from a Database]] - full mirror of `raw/reading-data-from-a-database.md`.
- [[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]] - full mirror of `raw/running-robokudo-in-a-docker-container.md`.

## Concepts

- [[concepts/robokudo|RoboKudo]] - framework-level mental model.
- [[concepts/pipelines|Pipelines]] - analysis engines as behavior-tree perception pipelines.
- [[concepts/annotators|Annotators]] - reusable behavior nodes that read and write perception annotations.
- [[concepts/annotator-configuration|Annotator Configuration]] - descriptors and parameter overrides.
- [[concepts/common-analysis-structure|Common Analysis Structure]] - shared CAS data model used by annotators.
- [[concepts/query-interface|Query Interface]] - action-based task interface for perception queries.
- [[concepts/behavior-tree-query-control|Behavior Tree Query Control]] - validation, feedback, cancellation, and preemption.
- [[concepts/database-storage|Database Storage]] - MongoDB-backed recording and replay.
- [[concepts/docker-usage|Docker Usage]] - GPU container workflow and display forwarding.
- [[concepts/package-structure|Package Structure]] - ROS package layout for RoboKudo extensions.

## Workflows

- [[workflows/run-demo-pipeline|Run Demo Pipeline]] - start RoboKudo and play sample data.
- [[workflows/create-package|Create Package]] - create and verify a custom RoboKudo package.
- [[workflows/create-annotator|Create Annotator]] - add a simple custom annotator.
- [[workflows/configure-annotator|Configure Annotator]] - add and override annotator parameters.
- [[workflows/run-query-workflow|Run Query Workflow]] - wire query receiving, interpretation, and result delivery.
- [[workflows/use-database-storage|Use Database Storage]] - record and replay sensor scenes through MongoDB.
- [[workflows/run-in-docker|Run in Docker]] - build and run the RoboKudo container.

## Reference

- [[reference/commands|Commands]] - ROS 2, Docker, and MongoDB command snippets from the tutorials.
- [[reference/code-entrypoints|Code Entrypoints]] - important modules, files, and APIs mentioned by the sources.
- [[reference/source-integrity|Source Integrity]] - mirror rules and verification commands.

## Questions

- No saved query answers yet.
