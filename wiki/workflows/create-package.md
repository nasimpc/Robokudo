---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
---

# Create Package

Use this workflow to create a custom RoboKudo package and verify that RoboKudo can run an analysis engine from it.

## Steps

1. Run `rk_create_package rk_tutorial` with the ROS-specific command.
2. Copy the core `demo.py` analysis engine into the package as `my_demo.py`.
3. Change the analysis engine `name` method to return `my_demo`.
4. Rebuild the workspace.
5. Source the workspace.
6. Start RoboKudo with `_ae=my_demo _ros_pkg=rk_tutorial`.

## See Also

- [[wiki/concepts/package-structure|Package Structure]]
- [[wiki/concepts/pipelines|Pipelines]]
- [[wiki/reference/commands|Commands]]
