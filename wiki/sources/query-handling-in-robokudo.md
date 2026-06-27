---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/query_interface.html
source_title: Query handling in RoboKudo
source_type: html
ingested: 2026-06-27
sources: []
---

# Query handling in RoboKudo

This tutorial introduces RoboKudo's Query Interface for triggering perception work from higher-level robot programs.

## Key Points

- Query handling has three parts: retrieve the query in the pipeline, interpret it inside annotators, and generate a result.
- `robokudo.annotators.query.QueryAnnotator()` is added after pipeline initialization to expose the query action server.
- When a query arrives, `QueryAnnotator` annotates it into the CAS and allows the pipeline to continue.
- Annotators inspect the current query through a predefined CAS view.
- Query answers are placed on the behavior-tree blackboard so the action server can return them to the caller.
- The tutorial also covers failure signaling and feedback during long-running queries.

## Connected Pages

- [[wiki/workflows/run-query-workflow|Run Query Workflow]]
- [[wiki/concepts/query-interface|Query Interface]]
- [[wiki/concepts/common-analysis-structure|Common Analysis Structure]]
- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]]
