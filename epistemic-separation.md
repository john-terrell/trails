---
type: concept
title: Epistemic Separation
aliases: [epistemic separation, evidence vs inference, four networks, facts vs beliefs]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/agent-memory, concept/epistemology]
confidence: medium
sources: 1
---

# Epistemic Separation

Keeping **what was observed**, **what was synthesized**, and **what is believed** in
structurally distinct stores, so that a reader — human or machine — can always tell which
of the three they are looking at. The organizing principle of [Hindsight](hindsight.md), whose critique
of the field is that existing systems *"blur the line between evidence and inference"*
([Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md), §1). Independently, and by different means, it is also
the organizing principle of this vault.

## Definition

Hindsight's implementation is a partition: **M = {W, B, O, S}**, with each fact stored in
exactly one network.

| | Store | Confidence | Shaped by disposition? |
|---|---|---|---|
| **W** world | objective external facts | no | no |
| **B** experience | the agent's own actions, first-person | no | no |
| **S** observation | entity summaries synthesized from W and B | **no** | **no** — *"preference-neutral"* |
| **O** opinion | subjective judgments `(text, c ∈ [0,1], τ)` | **yes** | **yes** |

The observation/opinion distinction is the subtle one and the paper is explicit about it
(§4.1.5): observations are generated *without* behavioral-profile influence and carry no
confidence score; opinions are formed *during* reflection, are shaped by
[Disposition Parameters](disposition-parameters.md), and carry one. Both are synthesized — only one is allowed to be
subjective.

## This vault's version

The same separation, implemented as conventions over plain files rather than as a partition
of a database:

| Hindsight | This vault |
|---|---|
| W — world facts | concept and entity pages, every claim citing a `src-` page |
| B — experience | `raw/notes/`, Log |
| S — observation | source pages and topic hubs' *Current understanding* |
| O — opinion | Contradictions assessments, [Overview](overview.md)'s "how firmly to hold this", `confidence:` frontmatter |
| confidence ∈ [0,1] | `confidence: high \| medium \| low` — **ordinal, not scalar** |
| (no equivalent) | `*(inference)*` inline tag — AGENTS §6.3 |
| (no equivalent) | `status: seed \| growing \| stable \| contested \| stale` |
| (no equivalent) | the immutable `raw/` layer |

Two of ours have no counterpart there, and both matter. **The `*(inference)*` tag** marks
the agent's own unsourced reasoning at the sentence level, so evidence and inference stay
distinguishable *within* a paragraph rather than only across stores. **The immutable raw
layer** means separation is anchored to something re-readable — which is what made the
Bush text correction possible when a second witness appeared. A memory graph of extracted
facts has no original to check against.

Conversely Hindsight has two we lack: **a scalar confidence** that can be arithmetically
updated, and **first-person experience as a distinct store** rather than notes in a folder.

## Why it matters

**It is the precondition for auditable belief revision.** If evidence and inference are
interleaved in one store, you cannot later determine which claims rested on which support —
so you cannot revise one without re-deriving everything. Both designs treat separation as
infrastructure for change over time, not as tidiness.

**It changes who can be wrong.** A system that records "Python is best for data science
(0.85)" as an *opinion* can be wrong without corrupting its facts. A system that records it
as a fact cannot. The vault's equivalent is `status: contested` and the
conflict register: a page can be flagged without its sources being
tainted.

**Convergence is weak evidence the principle is right.** Two designs built for different
consumers — an agent under a token budget, and a person reading in Obsidian — independently
separating evidence from inference suggests the distinction tracks something real rather
than one team's taste. Neither knew about the other.

## Criticisms and limits

- **Classification is an LLM call, and its error rate is unreported.** Hindsight assigns
  `ℓ(f) ∈ {world, experience, opinion, observation}` during extraction (§4.1.2, step 5).
  Nothing in the paper measures how often that is right. A fact misfiled as an opinion
  silently loses its evidential weight; an opinion misfiled as a fact silently gains one.
  The whole architecture rests on an unmeasured classifier.
- **"Exactly one network" may be too strict.** *"Alice is a software engineer at Google"*
  is plausibly both a world fact and an observation. The paper's own examples overlap.
- **Forced first-person opinions.** Appendix A.2 requires *"ALWAYS start with 'I think…',
  'I believe…'"* and *"NEVER use third-person."* That manufactures a subjective voice
  rather than recording one — separation implemented, then blurred by the register it's
  written in.
- **Ordinal confidence loses arithmetic and gains honesty.** Our `high/medium/low` cannot
  be updated by ±α, which is a real limitation if beliefs should move smoothly. But a
  scalar invites false precision: nothing calibrates 0.85 against 0.70, so the number
  means only that the model that produced it was more sure.
- **This vault's separation is conventional, not enforced.** `lint.py` checks that
  frontmatter exists and that `status:` values are valid; it cannot check that a sentence
  marked as fact is actually sourced. Hindsight's is enforced by the schema of its store.
  Convention decays; structure does not.

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) — primary; §1 (the critique), §3.1 (four networks),
  §4.1.1 (one network per fact), §4.1.5 (observations vs opinions), Appendix A.1–A.2
  (extraction and opinion prompts)

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **explains** [Opinion Reinforcement](opinion-reinforcement.md) — separation is what makes revision safe
- **contrasts** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — RAG is criticized precisely for lacking it
- **supports** [LLM Wiki Pattern](llm-wiki-pattern.md) — the pattern's source/page split is the same principle
- **implements** [Symbol Structuring](symbol-structuring.md) — an epistemic taxonomy is a symbol-structuring decision
- **supports** Contradictions — a register only works if beliefs are separable from evidence
