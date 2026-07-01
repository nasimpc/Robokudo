---
type: overview
status: active
created: 2026-06-28
updated: 2026-06-29
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

# RoboKudo Wiki Log

## [2026-06-28] ingest | Regenerated RoboKudo LLM wiki

Recreated the tracked top-level `wiki/` directory from the current converted RoboKudo markdown corpus in `raw/converted/robokudo-docs`.

- Copied all eight converted markdown files into `wiki/sources/` as full-content mirrors.
- Rebuilt the index, overview, concept pages, workflow pages, and reference pages for agent navigation.
- Added [[reference/source-integrity|Source Integrity]] to document the byte-for-byte mirror requirement.
- Updated root `AGENTS.md` to require future agents to start with [[index|RoboKudo Wiki Index]] and preserve source mirrors.

## [2026-06-28] ingest | Added tutorial overview node

Added [[tutorials/robokudo-tutorial-overview|RoboKudo Tutorial overview]] to connect the tutorial sequence shown in the upstream navigation. Added a missing-source metadata note for `Using RoboKudo within WSL` because `wsl_installation.html` is referenced by the raw HTML navigation but is absent from the captured corpus.

## [2026-06-29] lint | Fixed Obsidian tutorial graph links

Repointed generated wiki links from `wiki/...` targets to vault-root paths such as `sources/...` so the Obsidian vault under `wiki/` links to real notes instead of creating empty duplicate nodes. Removed the missing-source WSL placeholder note and the stray nested bad-link note.
