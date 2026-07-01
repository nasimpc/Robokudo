---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
---

# Create Package

Use this workflow to create a custom RoboKudo package named `rk_tutorial` and run a copied demo analysis engine from it.

## Steps

1. Run the package creation command for ROS 1 or ROS 2.
2. For ROS 2, install the package in editable mode if using that workflow.
3. Copy the built-in `demo.py` analysis engine to the new package as `my_demo.py`.
4. Build and source the workspace.
5. Run RoboKudo with `_ae=my_demo` and `_ros_pkg=rk_tutorial`.

## Source

- [[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]
