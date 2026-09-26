---
type: concept
title: Spreading Activation Retrieval
aliases: [spreading activation, graph retrieval, activation propagation]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/agent-memory, concept/information-retrieval]
confidence: medium
sources: 1
---

# Spreading Activation Retrieval

A retrieval channel that starts from what lexical and vector search *did* find and walks
outward along typed graph edges, so that material connected by entity, time or cause is
recovered even when it shares no words with the query. [Hindsight](hindsight.md)'s third recall channel
([Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md), §4.2.2), and — this is the interesting part — a formal
version of what this vault's topic hubs do by hand.

## Definition

Seed the graph with the top semantic hits, then propagate:

`A(fj, t+1) = max over (fi,fj,w,ℓ)∈E of [ A(fi, t) · w · δ · μ(ℓ) ]`

with `A(f, 0) = s_sem(Q, f)` for entry points and 0 elsewhere; `δ ∈ (0,1)` a decay factor;
and `μ(ℓ)` a **link-type multiplier** — *"Causal and entity edges have μ(ℓ) > 1, while weak
semantic or long-range temporal edges have μ(ℓ) ≤ 1."*

The stated purpose is exactly the failure we measured in our own search:

> This process surfaces memories that are not obviously similar to the query text but are
> connected through shared entities, nearby events, or causal chains.

The four edges it walks (TEMPR, §4.1.4): **temporal** (`w = exp(−Δt/σt)`), **semantic**
(cosine above threshold θs), **entity** (w = 1.0, bidirectional across memories sharing a
canonical entity), **causal** (LLM-extracted, typed `causes`/`caused_by`/`enables`/
`prevents`, w = 1.0, *"upweighted during traversal to favor explanatory connections"*).

## Why it matters here

**It validates the hub-as-recall-fallback rule with an independent design.** AGENTS §8
rung 6 says: when every search tier misses, read a **topic hub**, because a hub lists every
page in a domain with a one-line gloss. That rule was written after we measured BM25 *and*
reranked hybrid both missing `trail-blazer` for *"who should build the links between notes"*
(n=3), while both hubs listed it.

Hindsight reaches the same place from the other direction: don't rely on surface-form
matching, traverse from what you found to what's connected. **A topic hub is hand-built
spreading activation** — an agent curated the edges and wrote the glosses, so one read
recovers the neighbourhood. The difference is that theirs is automatic and weighted, ours is
authored and unweighted.

**It suggests what to automate.** Our hubs are written by judgment and go stale between
ingests. The entity edges are mechanically derivable from our `## Relations` blocks —
every `part-of`, `derives-from` and `contrasts` is a typed edge with a target. A script
could compute activation over that graph and propose hub entries. That is a concrete
follow-up, not a speculation. → Open Questions

**Causal weighting is a capability we lack entirely.** Our 11 relation types
([Typed Links](typed-links.md)) include `explains` but no `causes`/`enables`/`prevents`. Hindsight
upweights causal edges because they are the explanatory ones — which is what you want when
the question is "why", and most of this vault's questions are.

**Token budget rather than top-k.** Their `Recall(B, Q, k)` returns facts with `Σ|fi| ≤ k`.
Our ladder uses a soft prose budget (*"≤ ~5k tokens"*) with nothing enforcing it. A budget
is the right interface for an agent: it makes "how much can I afford to read" a parameter
rather than a discipline.

## Criticisms and limits

- **The channel is never ablated.** Table 3 reports whole-system scores. Nothing isolates
  graph retrieval's contribution, so the mechanism this page describes is justified by
  plausibility and a design argument, not by measurement.
- **Seeded from semantic hits, so it inherits their misses.** Activation starts at the top
  *semantic* results. If vector search fails on vocabulary mismatch — our measured failure
  mode — the walk starts from the wrong nodes. Hubs don't have this problem: they're read
  directly.
- **μ(ℓ), δ and θs are all unreported.** The multipliers that decide whether causal edges
  outrank semantic ones are parameters with no stated values, so the behaviour can't be
  reproduced from the paper.
- **Entity resolution is the load-bearing step and is heuristic.** `ρ(m) = argmax[α·sim_str
  + β·sim_co + γ·sim_temp]` with unstated coefficients. Merged entities create false edges;
  split entities sever real ones.
- **Our version is slower but explainable.** Reading a hub costs ~1.5k tokens and shows its
  reasoning as prose. Activation returns a score with no account of why an item surfaced —
  which matters when the consumer is a person who intends to disagree.

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) — primary; §4.1.4 (four link types and weights), §4.2.1
  (token-budget interface), §4.2.2 (the propagation equation and its rationale)

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **contrasts** [qmd](qmd.md) — three channels and a top-k vs four channels and a token budget
- **implements** [Associative Indexing](associative-indexing.md) — traversal over many-to-many links, automated
- **supports** [Typed Links](typed-links.md) — link types are what make μ(ℓ) weighting possible
- **explains** [N-Dimensional Projection Problem](n-dimensional-projection-problem.md) — traversal recovers structure serial media flatten
- **contrasts** [Personal Knowledge Management](personal-knowledge-management.md) — authored hubs vs computed activation
