---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/create_your_own_package.html
source_title: Create your own RoboKudo package
source_type: html
ingested: 2026-06-27
sources: []
---

# Create your own RoboKudo package

This tutorial creates a custom package named `rk_tutorial` and verifies it by adding a copied demo analysis engine named `my_demo`.

## Key Points

- RoboKudo extensions can live in separate ROS packages.
- The package generator is `rk_create_package`.
- Generated packages contain annotator code, descriptor code, analysis-engine definitions, and ROS/Python package metadata.
- The tutorial copies RoboKudo's `demo.py` analysis engine into the custom package and renames its `name` return value to `my_demo`.
- The workspace must be rebuilt and sourced before running the custom analysis engine.
- ROS 1 and ROS 2 have different package layouts and commands.

## Connected Pages

- [[wiki/workflows/create-package|Create Package]]
- [[wiki/concepts/package-structure|Package Structure]]
- [[wiki/concepts/pipelines|Pipelines]]
- [[wiki/reference/commands|Commands]]
