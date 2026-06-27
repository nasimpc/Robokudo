---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[wiki/sources/advanced-query-handling|Advanced Query Handling]]"
---

# Run Query Workflow

Use this workflow to expose a RoboKudo pipeline through the query interface.

## Basic Steps

1. Add `QueryAnnotator` after pipeline initialization.
2. Let the annotator receive and place incoming queries into the CAS.
3. In downstream annotators, inspect the current query through the query CAS view.
4. Create a query result.
5. Put the result on the behavior-tree blackboard for return to the action caller.
6. Add failure and feedback handling when the task is long-running or can fail.

## Advanced ROS 2 Steps

Use the advanced behavior-tree pattern when queries need validation, live feedback, cancellation, or preemption. The source tutorial names `query_complex.py`, `QueryFeedbackAndCount`, `ConditionalSelector`, `ActionServerNoPreemptRequest`, and `Inverter` as the relevant pieces.

## See Also

- [[wiki/concepts/query-interface|Query Interface]]
- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
