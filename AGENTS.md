# RoboKudo LLM Wiki Maintainer Guide

This workspace is an LLM-maintained personal wiki for RoboKudo notes.

## Layers

- `raw/sources/` contains immutable original source material. Read from it only for archival verification; do not edit these files.
- `raw/converted/` contains generated markdown mirrors of raw sources. Agents should prefer these converted files when they need source-level detail because they are easier to search and read than HTML.
- `wiki/` contains generated markdown maintained by the LLM.
- `.obsidian/` contains Obsidian vault settings and should be preserved.

## Required Workflow

Before answering substantive questions, read `wiki/index.md` first, then open the relevant pages. Prefer existing wiki pages for synthesized knowledge. If a page is missing detail, read the matching markdown mirror in `raw/converted/` before falling back to the original file in `raw/sources/`.

Do not treat `raw/converted/` as a manually curated wiki. It is a generated readability layer. If a converted file conflicts with its original source, trust `raw/sources/` and regenerate the converted file.

When ingesting a new source:

1. Add or place it under `raw/sources/`.
2. Create or regenerate a markdown mirror under `raw/converted/` when the source format is less agent-readable than markdown.
3. Create or update a source summary in `wiki/sources/`.
4. Update affected concept, workflow, and reference pages.
5. Add or update links between pages using full-path Obsidian links, for example `[[wiki/concepts/annotators|Annotators]]`.
6. Update `wiki/index.md`.
7. Append an entry to `wiki/log.md`.

When answering a query:

1. Search `wiki/index.md` and the relevant pages.
2. Cite wiki pages with Obsidian links.
3. If the answer is reusable, save it under `wiki/questions/` and add it to the index and log.

When linting:

- Check for broken links.
- Find orphan pages that are not linked from `wiki/index.md` or other pages.
- Look for claims that need source support.
- Flag contradictions between pages or between old wiki pages and newer sources.
- Suggest missing concept pages when important terms recur.

## Page Conventions

Every generated page should start with YAML frontmatter:

```yaml
---
type: concept
status: draft
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources:
  - "[[wiki/sources/source-page|Source title]]"
---
```

Allowed `type` values are `overview`, `source`, `concept`, `workflow`, `reference`, and `question`.

Use concise, factual prose. Prefer short sections, direct links, and task-oriented summaries. Do not paste long source excerpts unless a short quote is necessary. Raw sources remain the source of truth.

Converted source mirrors may use `type: converted-source` and `status: generated`. They are not wiki pages and do not need to be listed in `wiki/index.md`.

## Naming

- Use lowercase kebab-case filenames.
- Keep source summaries in `wiki/sources/`.
- Keep conceptual synthesis in `wiki/concepts/`.
- Keep step-by-step tasks in `wiki/workflows/`.
- Keep command/API/path lookups in `wiki/reference/`.
- Keep reusable answers in `wiki/questions/`.

## Logging

Append-only log entries in `wiki/log.md` must use parseable headings:

```markdown
## [YYYY-MM-DD] ingest | Title
## [YYYY-MM-DD] query | Title
## [YYYY-MM-DD] lint | Title
```

Do not rewrite prior log entries except to fix a clear typo.
