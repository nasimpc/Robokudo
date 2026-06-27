---
type: reference
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[wiki/sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[wiki/sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# ROS 1 vs ROS 2 Notes

## ROS 1

- Uses `roscore`.
- Runs RoboKudo with `rosrun robokudo main.py`.
- Plays sample data with `rosbag play`.
- Builds workspaces with `catkin build`.
- The Docker tutorial is tested for ROS 1.

## ROS 2

- Does not use `roscore`.
- Runs RoboKudo with `ros2 run robokudo_ros main`.
- Plays sample data with `ros2 bag play`.
- Builds workspaces with `colcon build --merge-install`.
- Advanced query handling is documented as ROS 2 only.

## Related

- [[wiki/reference/commands|Commands]]
- [[wiki/concepts/behavior-tree-query-control|Behavior Tree Query Control]]
