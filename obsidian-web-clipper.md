---
type: entity
title: Obsidian Web Clipper
aliases: [web clipper, Obsidian clipper]
created: 2026-09-26
updated: 2026-09-26
status: seed
tags: [entity/product, tooling, pkm]
confidence: medium
sources: 1
---

# Obsidian Web Clipper

A browser extension that converts web articles to markdown. In the
[LLM Wiki Pattern](llm-wiki-pattern.md) it is the recommended front door for getting sources into the raw
collection — the lowest-friction step in the whole pipeline, and therefore the one that
determines whether the corpus actually grows.

## Identity

| | |
|---|---|
| **Type** | product (browser extension) |
| **Upstream** | made for [Obsidian](obsidian.md) |
| **Role here** | source acquisition → `raw/clippings/` |

## What the corpus says

> Obsidian Web Clipper is a browser extension that converts web articles to markdown.
> Very useful for quickly getting sources into the raw collection.
> — [LLM Wiki](Sources.md)

## How it fits this vault's workflow

It is the entry point for step 1 of AGENTS.md §4. The intended flow:

1. Clip an article → it lands in **`raw/clippings/`** (the inbox; the only folder in
   `raw/` the agent may move files out of)
2. Companion tip from the same source: bind *Download attachments for current file* to
   `Ctrl+Shift+D` so clip images localize to `raw/assets/` instead of staying as remote
   URLs that rot. The attachment folder is already set to `raw/assets` in this vault;
   the hotkey binding is still to do by hand.
3. Tell the agent `ingest clippings/<file>` → it normalizes to `raw/sources/`, freezes
   the file, and propagates into the wiki.

`raw/clippings/` exists as a separate inbox precisely because clipper output is messy —
nav cruft, remote image URLs, inconsistent frontmatter — and `raw/sources/` is meant to
hold only clean, frozen files.

## Criticisms and limits

- **Clipper output needs normalization.** Which is why it goes to an inbox rather than
  straight into `sources/`.
- **The doc's caveat on images:** "LLMs can't natively read markdown with inline images
  in one pass — the workaround is to have the LLM read the text first, then view some or
  all of the referenced images separately." Clunky but workable, and encoded in
  AGENTS.md §4 step 2.

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — sole source; "Tips and tricks"

## Relations

- **implements** [LLM Wiki Pattern](llm-wiki-pattern.md) — the ingest front door into raw/clippings/
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
