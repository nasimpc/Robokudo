---
type: concept
status: draft
created: 2026-06-27
updated: 2026-06-27
sources:
  - "[[wiki/sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[wiki/sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
---

# Common Analysis Structure

The Common Analysis Structure, or CAS, is the shared data structure used by RoboKudo annotators. The tutorial describes it as a Python dictionary-like structure with predefined CAS views to keep data access consistent.

## Role

- Holds incoming sensor data and derived annotations.
- Lets annotators communicate without direct coupling.
- Stores the current query for query-aware annotators.

## Related

- [[wiki/concepts/annotators|Annotators]]
- [[wiki/concepts/query-interface|Query Interface]]
- [[wiki/workflows/create-annotator|Create Annotator]]
