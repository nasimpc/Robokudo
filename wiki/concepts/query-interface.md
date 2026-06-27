---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[wiki/sources/advanced-query-handling|Advanced Query Handling]]"
---

# Query Interface

The Query Interface lets higher-level robot programs trigger RoboKudo perception tasks at specific times instead of relying only on continuous perception.

## Basic Flow

1. Add `robokudo.annotators.query.QueryAnnotator()` after pipeline initialization.
2. Receive a query through the action server.
3. Annotate the query into the [[wiki/concepts/common-analysis-structure|Common Analysis Structure]].
4. Let annotators inspect and act on the query.
5. Place a query result on the behavior-tree blackboard for the action server to return.

## Related

- [[wiki/workflows/run-query-workflow|Run Query Workflow]]
- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]]
- [[wiki/concepts/annotators|Annotators]]
