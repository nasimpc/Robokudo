---
type: workflow
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/create-your-own-annotator|Create your own Annotator]]"
---

# Create Annotator

Use this workflow to add a minimal custom annotator to `rk_tutorial`.

## Steps

1. Create `my_first_annotator.py` under the package annotators directory.
2. Implement a class that inherits from `BaseAnnotator`.
3. Put the runtime behavior in `update`.
4. Access shared perception data through the CAS.
5. Import the annotator in `my_demo.py`.
6. Insert it into the analysis engine behavior tree.
7. Start the analysis engine and verify console output.

## See Also

- [[wiki/concepts/annotators|Annotators]]
- [[wiki/concepts/common-analysis-structure|Common Analysis Structure]]
- [[wiki/reference/code-entrypoints|Code Entrypoints]]
