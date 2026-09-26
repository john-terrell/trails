---
type: entity
title: Marp
aliases: [marp, Markdown Presentation Ecosystem]
created: 2026-09-26
updated: 2026-09-26
status: seed
tags: [entity/product, tooling, output-formats]
confidence: medium
sources: 1
---

# Marp

A markdown-based slide deck format, with an [Obsidian](obsidian.md) plugin. Named by
[the pattern doc](Sources.md) as one of the output forms a query
answer can take — the case where the useful response to a question is a presentation
rather than a page.

## Identity

| | |
|---|---|
| **Type** | product (format + tooling) |
| **Role here** | optional answer output format |
| **Installed?** | **No** — not present on this machine as of 2026-09-26 |

## What the corpus says

> Marp is a markdown-based slide deck format. Obsidian has a plugin for it. Useful for
> generating presentations directly from wiki content.

It appears in the query operation, where answers "can take different forms depending on
the question — a markdown page, a comparison table, a slide deck (Marp), a chart
(matplotlib), a canvas."

## Why it matters here

It is an instance of a general principle worth keeping visible: **the wiki is a
generation source, not just a store.** Because content is already structured into
linked pages with frontmatter, producing a deck is a transformation rather than fresh
authoring. Per AGENTS.md §8, a Marp deck is a `.md` file with `marp: true`
in frontmatter, filed to `wiki/answers/` like any other answer.

## Status in this vault

Not installed, and not needed yet — no deck has been requested. If one is: the
Obsidian community plugin plus `marp-cli` (`npm i -g @marp-team/marp-cli`) would be
required to export to PDF/PPTX. Recorded in Open Questions as a deferred decision,
consistent with the source's own "everything mentioned above is optional and modular."

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — sole source; one line in "Tips and tricks"

## See also

- [Obsidian](obsidian.md) — plugin host
- [Dataview](dataview.md) — the other optional output/query plugin
- AGENTS — §8, answer output formats
