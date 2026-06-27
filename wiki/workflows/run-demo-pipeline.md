---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
---

# Run Demo Pipeline

Use this workflow to start the built-in RoboKudo demo pipeline and feed it sample data.

## Steps

1. Download the test data for the ROS version in use.
2. For ROS 1, start `roscore`.
3. Start RoboKudo with the `demo` analysis engine.
4. Play the bag data in a loop.
5. Use the visualizer keyboard controls to inspect outputs such as `PointCloudClusterExtractor`.

## See Also

- [[wiki/reference/commands|Commands]]
- [[wiki/concepts/pipelines|Pipelines]]
