---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
---

# Behavior Tree Query Control

Advanced RoboKudo query handling uses behavior-tree control flow to validate, process, monitor, cancel, and preempt queries.

## Source Concepts

- `query_complex.py` is the full working example named by the tutorial.
- `QueryFeedbackAndCount` is the worker node used to demonstrate feedback and progress.
- `ConditionalSelector` is used for preemption handling.
- `ActionServerNoPreemptRequest` and `Inverter` help control whether preemption is allowed.
- This advanced flow is documented as ROS 2 only.

## Related

- [[wiki/concepts/query-interface|Query Interface]]
- [[wiki/workflows/run-query-workflow|Run Query Workflow]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
