---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# Docker Usage

The Docker tutorial runs RoboKudo inside a GPU-enabled container. It depends on NVIDIA container tooling and host display access for the 2D and 3D visualizers.

## Constraints

- The source says the tutorial is tested only for ROS 1.
- NVIDIA GPU support is expected.
- X11 access is granted from the host with `xhost local:root`.
- The container uses host networking and mounts `/tmp/.X11-unix`.

## Related

- [[wiki/workflows/run-in-docker|Run in Docker]]
- [[wiki/reference/commands|Commands]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
