---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# Run in Docker

Use this workflow to run RoboKudo inside the documented GPU-enabled Docker container.

## Steps

1. Build the image from the RoboKudo repository Dockerfile.
2. For ROS 1, start `roscore` outside the container.
3. Allow local root X11 access with `xhost local:root`.
4. Run the container with host networking, NVIDIA GPU flags, display variables, and `/tmp/.X11-unix` mounted.
5. Start RoboKudo inside the container.

The source says this tutorial is only tested for ROS 1. Treat the ROS 2 command as a starting point, not a validated Docker workflow.

## Source

- [[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]
