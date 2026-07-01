---
type: workflow
status: active
created: 2026-06-28
updated: 2026-07-01
sources:
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
---

# Create Package

Use this workflow to create a custom RoboKudo package named `rk_tutorial` and run a copied demo analysis engine from it.

## Steps

1. Run the ROS 2 package creation command.
2. Install the package in editable mode if using that workflow.
3. Copy the built-in `demo.py` analysis engine to the new package as `my_demo.py`.
4. Build and source the workspace.
5. Run RoboKudo with `_ae=my_demo` and `_ros_pkg=rk_tutorial`.

## Source

- [[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]
