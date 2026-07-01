---
type: concept
status: active
created: 2026-06-28
updated: 2026-06-29
sources:
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
---

# Common Analysis Structure

The Common Analysis Structure, or CAS, is the shared data object passed between annotators. The tutorials describe it as a Python dictionary-like structure with predefined keys in `CASViews`.

Annotators use the CAS to retrieve data such as point clouds and queries. Query handling adds the current query into a predefined CAS view so downstream annotators can inspect requested attributes.

## Related

- [[concepts/annotators|Annotators]]
- [[concepts/query-interface|Query Interface]]
