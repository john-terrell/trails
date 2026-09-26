---
type: entity
title: qmd
aliases: [QMD, Query Markup Documents, tobilu/qmd]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [entity/product, tooling, search]
confidence: high
sources: 1
---

# qmd

An on-device hybrid search engine for markdown, recommended by
[the pattern doc](Sources.md) as the scale path for wiki
search. Combines BM25 full-text search, vector semantic search, and LLM re-ranking,
all running locally. Exposes both a CLI — so an agent can shell out to it — and an
MCP server, so it can be a native tool. **Installed in this vault 2026-09-26.**

## Identity

| | |
|---|---|
| **Type** | product (CLI + MCP server, Rust/Node) |
| **Upstream** | [tobi/qmd](https://github.com/tobi/qmd) · npm `@tobilu/qmd` |
| **Version installed** | 2.8.3 |
| **Binary** | `~/.local/bin/qmd` |
| **Index** | `.qmd/index.sqlite` (project-local, gitignored) · config `.qmd/index.yml` (committed) |
| **Models** | ~2 GB GGUF in `~/.cache/qmd/models/` |
| **Runtime here** | better-sqlite3 + sqlite-vec; Metal GPU on Apple M2 Max |

## Why the pattern doc recommends it

> at small scale the index file is enough, but as the wiki grows you want proper
> search. qmd is a good option: it's a local search engine for markdown files with
> hybrid BM25/vector search and LLM re-ranking, all on-device.

Two properties matter for this vault. **Local** — a second brain containing journals
and personal material should not round-trip through a hosted embedding API. **Both
CLI and MCP** — an agent that can only use MCP tools is locked to one harness; a CLI
works from any shell.

Note the deliberate difference from [Retrieval-Augmented Generation](retrieval-augmented-generation.md): qmd retrieves
over *compiled wiki pages*, not raw chunks. It is retrieval infrastructure in service
of the compiled layer, not a substitute for it.

Run `qmd update && qmd embed` at the end of any operation that changed pages (§15).

> [!warning] The index is project-local
> `.qmd/index.sqlite` binds only when cwd is inside the vault. From any other directory,
> wrap calls in `(cd ~/Obsidian && qmd …)`. Do **not** use
> `QMD_CONFIG_DIR=<vault>/.qmd`: it reads the config — `qmd collection list` looks
> perfectly healthy — but binds the empty global index, so every search silently returns
> nothing. Diagnose with `qmd status` and check the `Index:` line.

## Commands used by this vault

```sh
qmd status                                   # index health, collection stats
qmd update                                   # re-index changed files
qmd embed                                    # generate vectors for new/changed docs
qmd query "<question>"                       # hybrid + rerank — best quality
qmd search "<keywords>"                      # BM25 only — fast, no model
qmd vsearch "<question>"                     # vector only
qmd query "<q>" --all --files --min-score 0.4  # file list for an agent
qmd get "wiki/concepts/memex.md"             # fetch one doc
qmd multi-get "wiki/sources/*.md"            # batch fetch by glob
```

Agent conventions from AGENTS.md §8 (amended by Schema Proposals #003):
**probe cheap, escalate only on miss.** Rung 1 is `qmd search -c wiki` (BM25, ~0.1 s);
`qmd query` is rung 5, reached only when rung 1 misses, because it costs 7–14 s and loads
~2 GB of models. `index.md` is rung 6 — the map, not the first move. `rg` handles exact
names, dates and quotes.

Two measured cautions. **Zero BM25 hits means vocabulary mismatch, not absence** —
"should knowledge trails be shared" returned no BM25 hits at all, yet Contradictions
C-002 is precisely about sharing trails.

And **reranking helps but is not a recall guarantee.** For *"did Bush solve who maintains
the trails"*, BM25 and hybrid-without-rerank both missed [Trail Blazer](trail-blazer.md) while the
reranked query ranked it 100%. For *"who should build the links between notes"*, all
three tiers missed that same page — it shares no vocabulary with the question. n=2,
2026-09-26. When every tier misses, fall back to the **map**: a topic hub lists each page
with a gloss, which is the recall mechanism search structurally lacks. See AGENTS §8
rungs 5–6.

## Collections configured

| Collection | Path | Context |
|---|---|---|
| `wiki` | `./wiki` | The compiled knowledge layer — authoritative for what this second brain believes |
| `raw` | `./raw` | Immutable source documents — quote from here, never modify |

Scoped search: `qmd query "x" -c wiki` or `-c raw`.

## Criticisms and limits

- **Installed ahead of need.** The doc says `index.md` suffices to ~100 sources; this
  vault has 1. The owner chose it anyway — reasonable (it's additive, and retrofitting
  embeddings later is more annoying), but the vault is now carrying ~2 GB of models and
  an index it does not yet need. Logged in Open Questions.
- **Embeddings lag the wiki.** Vectors are only as fresh as the last `qmd embed`. A
  page changed but not re-embedded will not be found semantically. This is a real
  failure mode and the reason §15 of AGENTS.md makes re-embedding part of
  "definition of done."
- **BM25 alone misses paraphrase; vectors alone miss exact terms.** Use `query`
  (hybrid) for real questions and `search` only when speed matters.
- **`.qmd/index.yml` trust gating.** A checked-in project config is not fully trusted
  by qmd: `update` hooks, collection paths pointing outside the project, and
  non-default model URIs are skipped in non-interactive contexts (agents, CI, MCP).
  This vault's config uses only in-project paths and default models, so nothing is
  gated — keep it that way.

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — "Optional: CLI tools" section. Everything else
  on this page comes from the installed tool's own docs and `qmd doctor` output
  (2026-09-26), not from the corpus. *(inference: flagged as outside-source detail)*

## Comparison: Hindsight's recall

[Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) §4.2 describes a retrieval layer that is a useful yardstick.
Hindsight runs **four** channels — semantic, BM25, graph ([Spreading Activation Retrieval](spreading-activation-retrieval.md)),
temporal — fused by RRF and cross-encoder reranked; qmd runs three of those four (no temporal
channel) with the same RRF + rerank design. The interfaces differ more importantly: Hindsight
takes a **token budget** `k` and returns facts with `Σ|fi| ≤ k`, while qmd takes `-n` results.
For an agent, a budget is the better primitive — it makes "how much can I afford to read" a
parameter rather than a discipline, which is what AGENTS §8's prose budget is trying to
express. → [How does this vault compare with Hindsight?](ans-2026-09-26-vault-vs-hindsight.md)

## Relations

- **implements** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — retrieval over compiled pages rather than raw chunks
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
