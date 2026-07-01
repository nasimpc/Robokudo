---
type: tutorial-index
status: active
created: 2026-06-28
updated: 2026-06-29
name: RoboKudo Tutorial overview
source_navigation: raw/sources/robokudo-docs/*.html toctree
source_corpus: raw/converted/robokudo-docs
tutorial_count: 8
available_source_mirrors: 8
missing_source_pages:
  - title: Using RoboKudo within WSL
    expected_source_file: raw/sources/robokudo-docs/wsl_installation.html
    status: not captured in current corpus
sources:
  - "[[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]"
  - "[[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]"
  - "[[sources/create-your-own-annotator|Create your own Annotator]]"
  - "[[sources/configure-your-annotator|Configure your Annotator]]"
  - "[[sources/query-handling-in-robokudo|Query handling in RoboKudo]]"
  - "[[sources/advanced-query-handling|Advanced Query Handling]]"
  - "[[sources/reading-data-from-a-database|Reading data from a Database]]"
  - "[[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]"
---

# RoboKudo Tutorial overview

This node connects the captured RoboKudo tutorial sequence shown in the upstream documentation navigation. The available tutorial source pages are full mirrors under `wiki/sources/`; the WSL tutorial is listed only as missing-source metadata because its source file is referenced by navigation but is not present in the current raw or converted corpus.

## Tutorial Sequence

1. [[sources/running-a-pipeline-in-robokudo|Running a pipeline in RoboKudo]]
2. [[sources/create-your-own-robokudo-package|Create your own RoboKudo package]]
3. [[sources/create-your-own-annotator|Create your own Annotator]]
4. [[sources/configure-your-annotator|Configure your Annotator]]
5. [[sources/query-handling-in-robokudo|Query handling in RoboKudo]]
6. [[sources/advanced-query-handling|Advanced Query Handling]]
7. [[sources/reading-data-from-a-database|Reading data from a Database]]
8. [[sources/running-robokudo-in-a-docker-container|Running RoboKudo in a Docker container]]

## Metadata Notes

- All linked tutorials have byte-for-byte source mirrors in `wiki/sources/`.
- `Using RoboKudo within WSL` is linked from the raw HTML table of contents as `wsl_installation.html`, but that HTML file is absent from `raw/sources/robokudo-docs` and no converted markdown mirror exists.
- Do not add a placeholder under `wiki/sources/` or `wiki/tutorials/` for the WSL page unless the actual converted source exists; `wiki/sources/` must stay an exact mirror of `raw/converted/robokudo-docs`.

## Related

- [[index|RoboKudo Wiki Index]]
- [[overview|RoboKudo Overview]]
- [[reference/source-integrity|Source Integrity]]
