---
type: workflow
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
---

# Create Annotator

Use this workflow to add a simple custom annotator to `rk_tutorial`.

## Steps

1. Create `my_first_annotator.py` in the package annotators directory.
2. Define `MyFirstAnnotator` as a `BaseAnnotator` subclass.
3. In `update`, retrieve the point cloud from the CAS and log its size.
4. Import the annotator in the analysis engine descriptor.
5. Insert it into the pipeline after preprocessing or clustering where the required CAS data exists.
6. Restart RoboKudo and check the log output.

## Source

- [[sources/create-your-own-annotator|Create your own Annotator]]
