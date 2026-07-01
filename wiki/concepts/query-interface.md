---
type: concept
status: active
created: 2026-06-28
updated: 2026-07-01
sources:
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
---

# Query Interface

The Query Interface lets external callers trigger perception work through the `/robokudo/query` ROS action server. A pipeline adds `robokudo.annotators.query.QueryAnnotator()` after `pipeline_init()` so incoming queries can be received, stored in the CAS, and used by downstream annotators.

Results are sent back with the ROS 2 `QueryHandler.send_answer` helper. The query tutorial also covers failure reporting and feedback queues.

## Related

- [[workflows/run-query-workflow|Run Query Workflow]]
- [[concepts/behavior-tree-query-control|Behavior Tree Query Control]]
