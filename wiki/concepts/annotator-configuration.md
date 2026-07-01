---
type: concept
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
---

# Annotator Configuration

Annotator configuration is handled through descriptor objects. A descriptor can declare class metadata and default parameters; a pipeline can instantiate a descriptor, override `parameters`, and pass it into an annotator constructor.

The corpus demonstrates this with `PointcloudCropAnnotator.Descriptor()` and explains that custom annotators can use the same pattern by adding a `Descriptor` class and accepting it during initialization.

## Related

- [[workflows/configure-annotator|Configure Annotator]]
- [[concepts/annotators|Annotators]]
