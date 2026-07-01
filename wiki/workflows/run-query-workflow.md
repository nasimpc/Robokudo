---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
---

# Run Query Workflow

Use this workflow to make a pipeline receive and answer perception queries.

## Steps

1. Add `QueryAnnotator()` directly after `pipeline_init()` in the analysis engine.
2. In downstream annotators, read the current query from the CAS query view.
3. Build a query result using `ObjectDesignator` and query result message types.
4. Send the answer through the ROS 1 blackboard key or the ROS 2 `QueryHandler` helper.
5. Report failures with the documented error handling decorator.
6. Optionally publish feedback through the query feedback queue.

For validation, cancellation, and preemption, use the ROS 2-only advanced query pattern in [[sources/advanced-query-handling|Advanced Query Handling]].
