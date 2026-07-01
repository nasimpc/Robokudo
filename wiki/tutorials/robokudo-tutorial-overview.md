---
type: tutorial-index
status: active
created: 2026-06-28
updated: 2026-07-01
name: RoboKudo Tutorial overview
source_navigation: historical upstream tutorial navigation
source_corpus: raw
tutorial_count: 8
available_source_mirrors: 8
missing_source_pages:
  - title: Using RoboKudo within WSL
    expected_source_file: raw/using-robokudo-within-wsl.md
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

This node connects the captured RoboKudo tutorial sequence. The available tutorial source pages are full mirrors under `wiki/sources/`; the WSL tutorial is listed only as missing-source metadata because no matching markdown source is present in the current `raw/` corpus.

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
- `Using RoboKudo within WSL` was referenced by earlier upstream navigation, but no matching markdown source exists in `raw/`.
- Do not add a placeholder under `wiki/sources/` or `wiki/tutorials/` for the WSL page unless the actual source markdown exists; `wiki/sources/` must stay an exact mirror of `raw/`.

## Related

- [[index|RoboKudo Wiki Index]]
- [[overview|RoboKudo Overview]]
- [[reference/source-integrity|Source Integrity]]
