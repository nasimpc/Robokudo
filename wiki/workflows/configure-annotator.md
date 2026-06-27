---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/configure-your-annotator|Configure your Annotator]]"
---

# Configure Annotator

Use this workflow to make an annotator configurable through descriptors.

## Steps

1. Add a `Descriptor` class to the annotator.
2. Add a nested `Parameters` class with default values.
3. Update the annotator constructor to accept a descriptor.
4. Pass the descriptor to `super().__init__`.
5. In the analysis engine, instantiate the descriptor and override parameter values.
6. Pass the descriptor to the annotator constructor.
7. Read parameters inside the annotator through `self.descriptor.parameters`.

## See Also

- [[wiki/concepts/annotator-configuration|Annotator Configuration]]
- [[wiki/concepts/annotators|Annotators]]
