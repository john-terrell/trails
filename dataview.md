---
type: entity
title: Dataview
aliases: [dataview, Obsidian Dataview]
created: 2026-09-26
updated: 2026-09-26
status: seed
tags: [entity/product, tooling, pkm]
confidence: medium
sources: 1
---

# Dataview

An [Obsidian](obsidian.md) community plugin that runs queries over page frontmatter, generating
dynamic tables and lists inside a note. Relevant to this vault because
AGENTS.md §6.1 puts structured YAML frontmatter on every page — which is
exactly what Dataview consumes.

## Identity

| | |
|---|---|
| **Type** | product (Obsidian community plugin) |
| **Role here** | dynamic views over wiki frontmatter |
| **Installed?** | **No** — community plugins are not enabled in this vault as of 2026-09-26 |

## What the corpus says

> Dataview is an Obsidian plugin that runs queries over page frontmatter. If your LLM
> adds YAML frontmatter to wiki pages (tags, dates, source counts), Dataview can
> generate dynamic tables and lists.

## Why the frontmatter convention exists regardless

The schema mandates frontmatter for every page — `type`, `status`, `tags`, `sources`,
`confidence`, `created`, `updated` — and Dataview is *one* consumer of it. Others that
work today without any plugin:

- `rg 'status: contested' -l wiki/` → every contested page
- `rg 'status: seed' -l wiki/` → every stub awaiting a source
- [qmd](qmd.md) metadata filtering, if the `qmd.metadata` block is ever adopted
- The lint pass (AGENTS.md §9 item 6) reads these fields to detect drift

So the convention pays off even if Dataview is never installed. If it is installed,
the obvious first views are: pages by `status`, pages sorted by `updated:` (staleness),
entities with `sources: 1` (thin pages), and source pages by `kind`.

## Criticisms and limits

- **A community plugin, not core.** Queries written in Dataview syntax are inert text
  anywhere else — GitHub, a plain editor, another agent's `read`. This is why
  AGENTS.md §12 keeps all wiki content readable as plain markdown and uses
  Dataview only for *generated views*, never for load-bearing content.
- **Duplicates information the agent already tracks.** `index.md` is a hand-maintained
  catalog; a Dataview table is a computed one. Both existing invites drift. If Dataview
  gets installed, decide whether `index.md` sections become generated or stay written.
  That decision belongs in Schema Proposals.

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — sole source; one line in "Tips and tricks"

## See also

- [Obsidian](obsidian.md) — plugin host
- [Marp](marp.md) — the other optional plugin
- Index — the hand-maintained catalog it could partly replace
- AGENTS — §6.1 frontmatter spec
