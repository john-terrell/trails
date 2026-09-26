---
type: concept
title: Narrative Fact Extraction
aliases: [narrative extraction, coarse-grained extraction, narrative facts]
created: 2026-09-26
updated: 2026-09-26
status: seed
tags: [concept/agent-memory]
confidence: medium
sources: 1
---

# Narrative Fact Extraction

[Hindsight](hindsight.md)'s choice to extract **few, large, self-contained** units rather than many
atomic ones: *"coarse-grained chunking, extracting 2–5 comprehensive facts per
conversation"*, each *"intended to cover an entire exchange rather than a single
utterance, be narrative and self-contained, include all relevant participants, and preserve
the pragmatic flow of the interaction"* ([Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md), §4.1.2).

## Definition

Their Figure 3 is the whole argument. From one conversation about naming a playlist:

| Fragmented (avoided) | Narrative (used) |
|---|---|
| "Bob suggested Summer Vibes" | *"Alice and Bob discussed naming their summer party playlist. Bob suggested 'Summer Vibes' because it is catchy and seasonal, but Alice wanted something more unique. Bob then proposed 'Sunset Sessions' and 'Beach Beats,' with Alice favoring 'Beach Beats' for its playful and fun tone. They ultimately decided on 'Beach Beats' as the final name."* |
| "Alice wanted something unique" | |
| "They considered Sunset Sessions" | |
| "Alice likes Beach Beats" | |
| "They chose Beach Beats" | |

Five facts become one. The stated benefit: retrieval and reasoning become *"less sensitive
to local segmentation decisions."* The pipeline that produces it runs coreference
resolution, temporal normalization ("last week" → absolute timestamps), participant
attribution, **preservation of explicit reasoning or justifications**, network
classification, and entity extraction over six types.

## Why it matters here

**It is an argument against atomic notes, and this vault is on the other side of it.**
[Hindsight](hindsight.md)'s own related-work survey describes **A-Mem** as using *"the Zettelkasten
method to create atomic notes with LLM-generated links that evolve over time"* — and
criticizes it for treating all memory uniformly. So the field contains a direct atomic-vs-
narrative disagreement, and our page size rule (AGENTS §3.8, 60–250 lines) sits closer
to narrative than to Zettelkasten.

The case for narrative units applies to us: a `{{Concept Name}}` that preserves *why* a
claim was made is more useful than five decontextualized bullets, and it survives being
retrieved alone. Our source pages' `## Key claims` sections already do this — each claim
carries its locator and a forward link, not just an assertion.

The case against, which the paper doesn't weigh: **narrative units are harder to revise.**
When new evidence contradicts one sentence inside a 200-word narrative fact, you rewrite the
whole unit. Atomic notes let you amend one and leave the rest. Our §4 rule — *"Update, don't
append… rewrite the affected prose into a coherent whole"* — accepts that cost deliberately,
and C-001 showed the benefit: the correction propagated cleanly because each page was a
coherent argument rather than an accumulation.

## Why this page is a seed

One source, one subsection, no ablation. The paper reports no comparison of narrative
versus fragmented extraction on its benchmarks — the choice is argued from Figure 3 and
asserted, not measured. Everything here rests on that.

## Sources

- [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) — primary; §4.1.2 and Figure 3. The A-Mem
  characterization is from §2.1, i.e. a competitor describing a competitor.

## Relations

- **part-of** [Agent Memory](agent-memory.md)
- **contrasts** [Symbol Structuring](symbol-structuring.md) — unit granularity is a symbol-structuring decision
- **supports** {{Source Title}} — self-contained units with preserved reasoning
- **derives-from** [Epistemic Separation](epistemic-separation.md) — classification happens during extraction
- **contrasts** [Maintenance Burden](maintenance-burden.md) — larger units cost more to revise, less to retrieve
