---
type: reference
status: active
created: 2026-06-28
updated: 2026-07-01
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

# Source Integrity

The `wiki/sources/` files are not summaries. They must remain exact mirrors of the current markdown source corpus in `raw/`.

## Mirror Rule

- Copy every root-level `.md` file from `raw/` into `wiki/sources/` without changing bytes.
- Do not add wiki-specific frontmatter, summaries, excerpts, or cleanup edits to source mirrors.
- Put synthesis only in `wiki/overview.md`, `wiki/concepts/`, `wiki/workflows/`, and `wiki/reference/`.

## Verification

```bash
diff -qr raw wiki/sources
wc -l raw/*.md wiki/sources/*.md
rg -n "T[O]DO|F[I]XME|py[c]ram|Py[C]RAM" wiki AGENTS.md
```

A link sanity check should parse Obsidian links like `[[concepts/annotators|Annotators]]` and verify that the target `.md` file exists.
