---
type: source
status: ingested
created: 2026-06-27
updated: 2026-06-27
source_file: raw/sources/robokudo-docs/configure_your_annotator.html
source_title: Configure your Annotator
source_type: html
ingested: 2026-06-27
sources: []
---

# Configure your Annotator

This tutorial explains descriptor-based annotator configuration using `PointCloudCropAnnotator`, then applies the same pattern to a custom annotator.

## Key Points

- Annotator parameterization lives in an annotator `Descriptor` class.
- Parameters are grouped under a `Parameters` subclass.
- Pipeline authors instantiate a descriptor, override parameter values, and pass the descriptor to the annotator constructor.
- Annotator code reads parameters through `self.descriptor.parameters.NAME_OF_PARAMETER`.
- The tutorial example adjusts pointcloud crop bounds such as `min_x`.

## Connected Pages

- [[wiki/workflows/configure-annotator|Configure Annotator]]
- [[wiki/concepts/annotator-configuration|Annotator Configuration]]
- [[wiki/concepts/annotators|Annotators]]
- [[wiki/reference/code-entrypoints|Code Entrypoints]]
