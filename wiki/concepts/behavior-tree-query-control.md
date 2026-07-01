---
type: concept
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
---

# Behavior Tree Query Control

Advanced query handling uses behavior-tree structure to validate incoming goals, publish feedback, produce results, and handle cancellation or preemption. The current advanced tutorial is explicitly ROS 2-only.

The documented `query_complex.py` pipeline uses query behaviors such as `QueryValidator`, `QueryFeedback`, `QueryResult`, `ActionServerNoPreemptRequest`, and selector/inverter logic to choose between normal completion and preemption handling.

## Related

- [[sources/advanced-query-handling|Advanced Query Handling]]
- [[concepts/query-interface|Query Interface]]
