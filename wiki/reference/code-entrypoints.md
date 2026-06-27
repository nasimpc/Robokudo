---
type: reference
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[wiki/sources/configure-your-annotator|Configure your Annotator]]"
  - "[[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[wiki/sources/advanced-query-handling|Advanced Query Handling]]"
---

# Code Entrypoints

## Files And Modules

- `descriptors/analysis_engines/` - analysis engine definitions, also called pipelines.
- `annotators/` - custom annotator implementations.
- `robokudo.annotators.core.BaseAnnotator` - base class for custom annotators.
- `robokudo.annotators.query.QueryAnnotator` - pipeline node that exposes the query action server.
- `robokudo.annotators.pointcloud_crop.PointCloudCropAnnotator` - source example for descriptor-based parameters.
- `robokudo_msgs.msg.QueryResult` and `robokudo_msgs.action.Query` - query result/action types mentioned by the query tutorial.
- `py_trees.blackboard.Blackboard` - behavior-tree blackboard used for query results.
- `query_complex.py` - advanced ROS 2 query-handling example named by the source.

## Related

- [[wiki/concepts/annotators|Annotators]]
- [[wiki/concepts/query-interface|Query Interface]]
- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]]
