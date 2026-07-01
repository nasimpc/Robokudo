---
type: workflow
status: active
created: 2026-06-28
updated: 2026-07-01
sources:
  - "[[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# Run in Docker

Use this workflow to run RoboKudo inside the documented GPU-enabled Docker container.

## Steps

1. Build the image from the RoboKudo repository Dockerfile.
2. Allow local root X11 access with `xhost local:root`.
3. Run the container with host networking, NVIDIA GPU flags, display variables, and `/tmp/.X11-unix` mounted.
4. Start RoboKudo inside the container with ROS 2 commands.

## Source

- [[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]
