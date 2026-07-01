# RoboKudo LLM Wiki Maintainer Guide

This workspace is an LLM-maintained personal wiki for RoboKudo notes.

## Required First Step

Before answering substantive questions or editing the wiki, read `wiki/index.md` first. Use it as the navigation catalog for source mirrors, concepts, workflows, and references.

## Source Corpus

- `raw/` contains the canonical RoboKudo markdown source corpus for the current wiki. Treat root-level `raw/*.md` files as source material; do not edit them unless the user explicitly asks for source maintenance or regeneration.
- `wiki/sources/` must contain byte-for-byte full-content mirrors of the markdown files in `raw/`.
- `wiki/` contains the Obsidian vault plus generated navigation, synthesis, workflow, and reference pages maintained by agents.
- `wiki/.obsidian/` contains Obsidian vault settings and should be preserved.

Some source files may retain generated-source frontmatter such as `source_file` values that refer to historical HTML inputs. Do not rewrite that metadata inside `raw/` or `wiki/sources/` unless the source corpus itself is being regenerated.

## Source Mirror Rule

Never replace a `wiki/sources/*.md` full mirror with a summary. Do not add wiki-specific frontmatter, excerpts, cleanup edits, or commentary to source mirrors. If the source corpus changes, copy the root-level markdown files from `raw/` into `wiki/sources/` again and verify with `diff -qr raw wiki/sources`.

## Required Workflow

When ingesting or regenerating RoboKudo docs:

1. Treat root-level `raw/*.md` files as the source corpus for markdown content.
2. Copy every source markdown file into `wiki/sources/` as a full mirror.
3. Update affected concept, workflow, and reference pages.
4. Use vault-root Obsidian links because `wiki/` is the Obsidian vault root, for example `[[concepts/annotators|Annotators]]`.
5. Update `wiki/index.md`.
6. Append an entry to `wiki/log.md`.
7. Run mirror, line-count, wrong-domain, and Obsidian-link checks.

When answering a query:

1. Read `wiki/index.md` first.
2. Open the relevant synthesis pages.
3. If source-level detail matters, open the matching full mirror in `wiki/sources/` or the matching source file in `raw/`.
4. Cite wiki pages with Obsidian links when helpful.

## Page Conventions

Generated synthesis pages should start with YAML frontmatter using one of these `type` values: `overview`, `concept`, `workflow`, `reference`, `tutorial-index`, `tutorial`, or `question`.

Source mirrors may use `type: converted-source` and `status: generated` because that frontmatter comes from the source corpus. Do not edit it manually in `wiki/sources/`.

Use lowercase kebab-case filenames. Keep source mirrors in `wiki/sources/`, tutorial sequence metadata in `wiki/tutorials/`, conceptual synthesis in `wiki/concepts/`, step-by-step tasks in `wiki/workflows/`, command/API/path lookups in `wiki/reference/`, and reusable answers in `wiki/questions/`.

## Logging

Append-only log entries in `wiki/log.md` must use parseable headings:

```markdown
## [YYYY-MM-DD] ingest | Title
## [YYYY-MM-DD] query | Title
## [YYYY-MM-DD] lint | Title
```

Do not rewrite prior log entries except to fix a clear typo.
