---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/docker_rk.html
source_title: Running RoboKudo in a Docker container
source_type: html
ingested: 2026-06-27
sources: []
---

# Running RoboKudo in a Docker container

This tutorial builds and runs RoboKudo in a Docker container with NVIDIA GPU support and host X11 display access.

## Key Points

- The tutorial requires NVIDIA container tooling and is tested for ROS 1.
- The Docker image is built from the RoboKudo repository Dockerfile.
- X11 access is granted with `xhost local:root` for the current login session.
- The container is run with host networking, GPU access, display variables, and `/tmp/.X11-unix` mounted.
- RoboKudo visualizers require graphics support from inside the container.
- The tutorial notes that `roscore` is not part of ROS 2.

## Connected Pages

- [[wiki/workflows/run-in-docker|Run in Docker]]
- [[wiki/concepts/docker-usage|Docker Usage]]
- [[wiki/reference/commands|Commands]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
