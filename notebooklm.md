---
type: entity
title: NotebookLM
aliases: [notebooklm, Notebook LM]
created: 2026-09-26
updated: 2026-09-26
status: seed
tags: [entity/product, llm-agents]
confidence: low
sources: 1
---

# NotebookLM

Named once in [the pattern doc](Sources.md) as an example of the
[RAG](retrieval-augmented-generation.md) approach the [LLM Wiki Pattern](llm-wiki-pattern.md) is contrasted
against — alongside ChatGPT file uploads and "most RAG systems."

## Identity

| | |
|---|---|
| **Type** | product |
| **Role in this wiki** | foil / point of comparison |
| **Approach** | [RAG](retrieval-augmented-generation.md) per the source |

## What the corpus actually says

One clause: "NotebookLM, ChatGPT file uploads, and most RAG systems work this way" —
where "this way" is retrieving chunks at query time so that "the LLM is rediscovering
knowledge from scratch on every question."

That is the entire basis for this page. No vendor, pricing, feature set, or
independent evaluation is in the corpus.

## Why this page is a seed

It exists because the source names it and it is likely to recur — the RAG-vs-wiki
comparison will come up again, and a red link is worse than a stub. It is *not* a
characterization of the product. If this vault ever needs a real assessment of
NotebookLM, the fix is to ingest a primary source about it, not to expand this page
from memory. Per AGENTS.md §3, no unsourced claims.

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — sole source; one clause, used as a foil

## Relations

- **instance-of** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — cited as an example of the approach
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
