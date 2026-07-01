---
type: concept
status: active
created: 2026-06-28
updated: 2026-07-01
sources:
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
---

# Package Structure

Custom RoboKudo functionality can live in a separate ROS package such as `rk_tutorial`. The package generator creates folders for annotators and descriptors, including analysis engine descriptors.

For ROS 2, the generated package supports adding custom annotators and analysis engines that depend on RoboKudo core packages. Install the package in editable mode when following the documented ROS 2 workflow.

## Related

- [[workflows/create-package|Create Package]]
- [[workflows/create-annotator|Create Annotator]]
