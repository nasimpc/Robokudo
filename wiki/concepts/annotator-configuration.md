---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/configure-your-annotator|Configure your Annotator]]"
---

# Annotator Configuration

RoboKudo annotators use descriptor classes for parameterization. A descriptor contains metadata and a nested `Parameters` class whose attributes become runtime configuration.

## Pattern

1. Define a `Descriptor` class on the annotator.
2. Add configurable values under `Descriptor.Parameters`.
3. In the analysis engine, instantiate the descriptor and override parameter values.
4. Pass the descriptor to the annotator constructor.
5. Read values inside the annotator with `self.descriptor.parameters.NAME_OF_PARAMETER`.

## Example Context

The source tutorial uses `PointCloudCropAnnotator` to show crop bounds such as `min_x`, then asks the reader to apply the same pattern to a custom annotator.

## Related

- [[wiki/workflows/configure-annotator|Configure Annotator]]
- [[wiki/concepts/annotators|Annotators]]
