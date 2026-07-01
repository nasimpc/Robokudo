---
type: reference
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[sources/reading-data-from-a-database|Reading data from a Database]]"
  - "[[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# ROS 1 vs ROS 2 Notes

The source corpus mixes ROS 1 and ROS 2 instructions. Check the source mirror for exact context before applying a command.

## Startup

- ROS 1 uses `roscore`; ROS 2 does not.
- ROS 1 commonly uses `rosrun robokudo main.py _ae=...`.
- ROS 2 commonly uses `ros2 run robokudo_ros main _ae=...`.

## Workspaces

- ROS 1 examples use `~/robokudo_ws`, `catkin build`, and `source ~/robokudo_ws/devel/setup.bash`.
- ROS 2 examples use `~/ros2_ws`, `colcon build --merge-install`, and `source ~/ros2_ws/install/setup.bash`.

## Bags

- ROS 1 sample data is a `.bag` file played with `rosbag play`.
- ROS 2 sample data is unpacked from `test.tar.gz` and played with `ros2 bag play`.

## Query Interface

- ROS 1 examples use actionlib tooling and blackboard answer delivery.
- ROS 2 examples use `ros2 action send_goal`, `robokudo_msgs.action.Query`, and `QueryHandler`.
- Advanced query handling in this corpus is explicitly ROS 2-only.

## Docker

- The Docker tutorial says it is only tested for ROS 1, even though it notes ROS 2 differences and shows a ROS 2 run command.
