---
type: topic
title: Agent Memory
aliases: [agent memory, LLM agent memory, memory systems]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [topic, agent-memory]
confidence: medium
sources: 1
---

# Agent Memory

The engineering discipline of giving an LLM agent persistent memory across sessions —
what to retain, how to organize it, how to recall it under a token budget, and how beliefs
change when new evidence arrives. Distinct from [Personal Knowledge Management](personal-knowledge-management.md), which
is about what a *person* knows, and from [Augmenting Human Intellect](augmenting-human-intellect.md), which is about
the whole human-plus-tool system. Agent memory asks a narrower and more tractable
question: how should a machine remember?

This hub exists because the vault acquired its first source in the category on
2026-09-26, and because that source turns out to be a **design foil**: it automates
several things this vault deliberately keeps human.

## Core concepts

- [Epistemic Separation](epistemic-separation.md) — keeping evidence, summaries and beliefs structurally distinct; the field's central claim
- [Opinion Reinforcement](opinion-reinforcement.md) — automatic belief revision by confidence increment; the direct contrast to AGENTS §5
- [Spreading Activation Retrieval](spreading-activation-retrieval.md) — graph traversal from search hits to connected memories; our hubs do this by hand
- [Narrative Fact Extraction](narrative-fact-extraction.md) — coarse-grained self-contained facts rather than atomic snippets
- [Disposition Parameters](disposition-parameters.md) — skepticism, literalism, empathy as configured belief-shapers

## Key entities

- [Hindsight](hindsight.md) — the system; Vectorize.io, MIT-licensed, four networks and three operations
- [qmd](qmd.md) — this vault's retrieval layer, for comparison

## Adjacent hubs

- [Personal Knowledge Management](personal-knowledge-management.md) — same problem, human as the consumer rather than the agent
- [Augmenting Human Intellect](augmenting-human-intellect.md) — the broader frame both sit inside

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) (2025-12, **primary but vendor-authored**) — the
  architecture, the benchmarks, and a map of eight competing systems. No limitations
  section; baselines largely not independently run. → Contradictions C-003, C-004

**Described secondhand in that source, not yet ingested:** MemGPT, LIGHT, Zep, **A-Mem**,
Mem0, Memory-R1, MemVerse, KARMA, Supermemory, Backboard, Memobase, LangMem. A-Mem is the
priority — it uses the **Zettelkasten** method with LLM-generated evolving links, making it
the nearest published relative to this vault.

## Current understanding

**The field's core insight is one this vault already reached independently.** Hindsight's
thesis is that existing systems *"blur the line between evidence and inference"*, and its
fix is to partition memory into four networks — world facts, agent experiences, entity
observations, and opinions carrying a confidence score. This vault does the same thing with
different machinery: `status:` and `confidence:` frontmatter, an `*(inference)*` tag for
unsourced reasoning, source pages separated from concept pages, and a
conflict register. Both designs conclude that **provenance must be
structural, not incidental**. Neither arrived by way of the other.

**Where the two designs genuinely diverge is belief revision.** Hindsight revises
automatically: an LLM classifies new evidence as `{reinforce, weaken, contradict, neutral}`
and confidence moves by ±α (−2α for contradiction), optionally rewriting the opinion's text.
Background merging *"resolves direct conflicts in favor of the new information."* This
vault forbids exactly that — AGENTS §5: *"Never overwrite a claim because a newer source
disagrees"* — and requires a human ruling. **C-001 is the concrete argument**: the newer
source misdescribed the older one, so recency-wins would have preserved the error.
→ [Opinion Reinforcement](opinion-reinforcement.md), Contradictions C-003

**On retrieval, Hindsight is ahead and its lead is instructive.** Four parallel channels
(semantic, BM25, graph, temporal), RRF-fused, cross-encoder reranked, trimmed to a **token
budget rather than a top-k**. This vault has three of those channels via [qmd](qmd.md) and no
temporal one, and we *measured* that both BM25 and reranked hybrid miss pages on vocabulary
mismatch. Their graph channel is [Spreading Activation Retrieval](spreading-activation-retrieval.md) — traverse from what you
found to what's connected — which is precisely what our topic hubs do by hand. That is a
real validation of the hub-as-recall-fallback rule in AGENTS §8 rung 6, and a hint that
hubs could be partly automated.

**The measurement gap is now visible, and embarrassing.** This vault has been complaining
that its corpus measures nothing. Hindsight reports an ablation that isolates its own
contribution — same OSS-20B backbone, 39.0% full-context versus 83.6% with the memory layer.
That is the design our `open-questions` has been asking for: hold the model constant, vary
the architecture. We could run the analogue on this vault and have not.

**How firmly to hold this.** One source, vendor-authored, with no limitations section,
benchmarks on *conversational* memory only, and comparison numbers largely taken from
competitors' own reports. The architectural ideas are credible and independently
corroborated by our own design convergence. The performance claims are not yet anything
this vault should repeat as fact.

## Tensions and open questions

- **Automatic vs adjudicated belief revision** — C-003, open. Not an abstract preference:
  the corpus contains a worked counterexample to recency-wins.
- **Does the four-network split apply to a human-read wiki?** Opinions and observations are
  separate networks there; here they are sections within pages. Which is better for a corpus
  a person reads is untested.
- **Can spreading activation replace hand-built hubs?** Their graph channel is automated
  from entity and causal links. Ours requires an agent to write a hub. → Open Questions
- **Nothing in this domain evaluates long-document knowledge.** Every benchmark is dialogue.
  Whether four networks help when retaining a 144-page technical report is unknown.

## Relations

- **part-of** [Augmenting Human Intellect](augmenting-human-intellect.md)
- **derives-from** [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md)
- **contrasts** [Personal Knowledge Management](personal-knowledge-management.md) — the agent is the consumer there, the human here; siblings under the same parent hub, not parent and child
