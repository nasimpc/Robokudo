---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/Advanced_query_handling.html
source_title: Advanced Query Handling
source_type: html
ingested: 2026-06-27
sources: []
---

# Advanced Query Handling

This ROS 2 tutorial extends basic query handling with validation, live feedback, cancellation, and behavior-tree preemption.

## Key Points

- The tutorial assumes familiarity with basic [[wiki/concepts/query-interface|Query Interface]] usage.
- It explains a behavior-tree pipeline that validates, processes, monitors, and cancels queries.
- Important concepts include query messages, feedback messages, result messages, worker nodes, and action-server behavior.
- The full working example is `query_complex.py`.
- `QueryFeedbackAndCount` is presented as the worker node.
- Preemption is handled with behavior-tree control nodes including `ConditionalSelector`, `ActionServerNoPreemptRequest`, and `Inverter`.
- The tutorial includes an action-client test path.

## Connected Pages

- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]]
- [[wiki/concepts/query-interface|Query Interface]]
- [[wiki/workflows/run-query-workflow|Run Query Workflow]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
