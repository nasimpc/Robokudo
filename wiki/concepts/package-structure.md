---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
---

# Package Structure

RoboKudo supports custom perception code in separate ROS packages. The tutorial package is named `rk_tutorial`.

## Important Directories

- `annotators/` holds custom annotator implementations.
- `descriptors/analysis_engines/` holds pipeline definitions.
- ROS 1 examples place code under `src/rk_tutorial/`.
- ROS 2 examples use a flatter Python package layout under `rk_tutorial/`.
- `package.xml`, `setup.py`, and, for ROS 2, `setup.cfg` carry package metadata and install configuration.

## Related

- [[wiki/workflows/create-package|Create Package]]
- [[wiki/concepts/pipelines|Pipelines]]
- [[wiki/concepts/annotators|Annotators]]
