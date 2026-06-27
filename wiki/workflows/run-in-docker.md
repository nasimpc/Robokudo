---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# Run in Docker

Use this workflow to build and run RoboKudo in a Docker container with GPU and display support.

## Steps

1. Install NVIDIA container tooling on the host.
2. Build the RoboKudo Docker image from the RoboKudo repository.
3. Allow root-owned local X11 clients for the login session with `xhost local:root`.
4. For ROS 1, start `roscore` on the host.
5. Run the container with host networking, GPU access, display environment, and the X11 socket mount.
6. Start RoboKudo inside the container.

## See Also

- [[wiki/concepts/docker-usage|Docker Usage]]
- [[wiki/reference/commands|Commands]]
- [[wiki/reference/ros1-vs-ros2-notes|ROS 1 vs ROS 2 Notes]]
