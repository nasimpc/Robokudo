---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/run_pipeline.html
source_title: Running a pipeline in RoboKudo
source_type: html
ingested: 2026-06-27
sources: []
---

# Running a pipeline in RoboKudo

This tutorial starts a basic RoboKudo perception pipeline after installation. It uses sample ROS bag data and the built-in `demo` analysis engine.

## Key Points

- A RoboKudo pipeline is an [[wiki/concepts/pipelines|analysis engine]] defined under `descriptors/analysis_engines`.
- The tutorial asks the user to download test data, start ROS infrastructure where needed, run RoboKudo with `_ae=demo`, and play the bag file in a loop.
- ROS 1 uses `roscore`, `rosrun robokudo main.py _ae=demo`, and `rosbag play`.
- ROS 2 uses `ros2 run robokudo_ros main _ae=demo` and `ros2 bag play`; `roscore` is not needed.
- The visual output is split between a 2D OpenCV-style visualizer and a 3D Open3D pointcloud visualizer.

## Connected Pages

- [[wiki/workflows/run-demo-pipeline|Run Demo Pipeline]]
- [[wiki/concepts/pipelines|Pipelines]]
- [[wiki/reference/commands|Commands]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
