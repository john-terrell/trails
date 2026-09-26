---
type: concept
title: Maintenance Burden
aliases: [bookkeeping cost, wiki decay, the maintenance problem]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/pkm, concept/labor, concept/history]
confidence: high
sources: 2
---

# Maintenance Burden

The cost of the bookkeeping that keeps a knowledge base coherent — updating
cross-references, keeping summaries current, noticing when new information contradicts
old claims, maintaining consistency across many pages. The pattern doc identifies it
as *the* reason personal wikis get abandoned, and removing it as the entire
contribution of [LLM Wiki Pattern](llm-wiki-pattern.md).

> [!note] Corrected by primary text — C-001 **resolved** 2026-09-26
> [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) claims [Vannevar Bush](vannevar-bush.md) *"couldn't solve"* who
> does this work. The primary text says otherwise: Bush proposes *"a new profession of
> [trail blazers](trail-blazer.md), those who find delight in the task of establishing
> useful trails through the enormous mass of the common record"*
> ([As We May Think](Sources.md), §8). He staffed the problem; he did
> not automate it. **The owner ruled for the primary text.** Register: Contradictions
> C-001.

## Definition

Crucially, it is **not** the reading or the thinking:

> The tedious part of maintaining a knowledge base is not the reading or the thinking
> — it's the bookkeeping.
> — [LLM Wiki](Sources.md)

It is the gap between adding a piece of knowledge and *integrating* it. Adding is cheap
and satisfying; integrating is expensive and invisible. Humans reliably do the first
and skip the second, which is why note collections grow while their usefulness stays
flat.

## The failure dynamic

> Humans abandon wikis because the maintenance burden grows faster than the value.

The mechanism, stated plainly: burden scales with the **number of pages that could
need updating** when something changes — roughly superlinear in corpus size, since a
new fact may bear on many existing pages. Value scales with how much of the corpus is
actually *coherent* — which depends on the maintenance being done. Once the owner
starts skipping updates, value growth slows while burden keeps climbing, and the
project dies. Abandonment is the predictable equilibrium, not a personal failing.

## Why it matters

This is the load-bearing claim of the whole pattern. If wikis failed for lack of
interest or lack of material, an LLM maintainer would not help. They fail for lack of
labor on a specific, tedious, well-defined class of task — precisely what an agent
does reliably:

> LLMs don't get bored, don't forget to update a cross-reference, and can touch 15
> files in one pass. The wiki stays maintained because the cost of maintenance is
> near zero.

It also explains the [Memex](memex.md)'s 80-year delay — though not for the reason the pattern
doc gives. Bush's design was not wrong, and he was not silent about staffing it; he
proposed [trail blazers](trail-blazer.md). What he could not do was make the work cheap
enough for **one person** to do alone, at useful volume, over a private corpus. That is
the actual gap [LLM Wiki Pattern](llm-wiki-pattern.md) fills. See Contradictions C-001.

## Three answers to the same problem

The corpus now holds three distinct strategies for maintenance burden, and they are not
variants of one idea:

| Strategy | Source | Who does the work | Evidence it works |
|---|---|---|---|
| **Staff it** — a profession who enjoy it | [As We May Think](Sources.md) §8 | [Trail blazers](trail-blazer.md) | None; one sentence, never built |
| **Distribute it** — a community of volunteers | [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) | Fans, editors | **Strong** — [Tolkien Gateway](tolkien-gateway.md) and every surviving wiki |
| **Automate it** — an agent under a schema | [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) | An LLM, directed by one owner | This vault, n=1, one day old |

The pattern doc presents automation as the answer to a problem Bush left open. The
primary text shows Bush had an answer, and that a third answer — distribution — has by
far the best track record. Automation is the newest and least-tested of the three, not
the only one.

## The economics of timing

Bush supplies a sharper version of the pattern doc's central argument than the pattern
doc does. His §1 case is that sound ideas fail on economics, not on merit:

- Leibnitz's calculating machine *"embodied most of the essential features of recent
  keyboard devices, but it could not then come into use. The economics of the situation
  were against it: the labor involved in constructing it … exceeded the labor to be
  saved by its use."*
- Babbage's engine: *"His idea was sound enough, but construction and maintenance costs
  were then too heavy."*
- The turning point: *"The world has arrived at an age of cheap complex devices of great
  reliability; and something is bound to come of it."*

Substitute *maintenance* for *construction* and this is exactly
[LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md)'s claim about the [Memex](memex.md) — the idea was always
viable, the labor was never affordable, and the affordability changed. Bush's version is
better than the pattern doc's because it is **general**: it explains a class of stalled
ideas rather than asserting one. It also implies a test the pattern doc never runs — if
the bottleneck was cost, then the value of automating depends on how expensive the
manual version actually was, which is measurable and has not been measured.

Practical consequence for this vault: **the ingest workflow's propagation step is the
product.** Writing a source summary is the easy 20%. Steps 5–7 of
AGENTS.md §4 — updating every entity, concept, topic, and synthesis page
the source touches — are the part that defeats humans and the part that must not be
skipped. A source that touches 2 pages instead of 12 is a failed ingest.

## Evidence

Strong on plausibility, thin on measurement. The source offers no data on wiki
abandonment rates. What it offers is a mechanism that matches widely-recognized
experience, plus [Tolkien Gateway](tolkien-gateway.md) as a counter-case: fan wikis *do* survive, because
a community distributes the burden across many maintainers. That supports the diagnosis
— it is burden, not interest, that kills them — while suggesting distribution as an
alternative solution to removal.

## Criticisms and limits

- **"Near zero" overstates it.** Burden shifts to *review*. An owner who doesn't check
  what the agent wrote inherits errors instead of doing bookkeeping; one who checks
  carefully has traded tedious work for attentive work. The honest claim is that
  burden moves from production to verification, where it is cheaper but not free.
- **Unmeasured against the alternative.** The doc never compares a maintained-by-LLM
  wiki to a simpler pile of notes plus [RAG](retrieval-augmented-generation.md). For
  some corpora the pile wins.
- **Consistency is not correctness.** An agent that touches 15 files in one pass can
  propagate a mistake across 15 files in one pass. Burden removal increases the blast
  radius of a bad ingest — which is why the Contradictions register and lint passes
  exist.
- **The human role may atrophy.** If the agent does all synthesis, the owner's
  understanding of their own corpus may weaken. The doc assigns the human "think about
  what it all means" but supplies no mechanism protecting that time.

## Instances and applications

- AGENTS.md §4 step 5 (propagation) and §9 (lint) — this vault's answer to
  the burden
- `## What this changes` on every source page — a forcing function for integration
- Log — pages-touched counts make skipped propagation visible

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — the "Why this works" section is largely an
  elaboration of this concept; its claim about Bush is **contradicted** by C-001
- [As We May Think](Sources.md) — primary; §1 on the economics of stalled ideas, §8 on
  [trail blazers](trail-blazer.md) as the answer to maintenance labor

## See also

- [Trail Blazer](trail-blazer.md) — Bush's answer, and the contradiction it creates
- [LLM Wiki Pattern](llm-wiki-pattern.md) — the automation answer
- [Memex](memex.md) — the design this problem stalled
- [Repetitive vs Creative Thought](repetitive-vs-creative-thought.md) — which part of the work is delegable at all
- [Knowledge Compounding](knowledge-compounding.md) — what maintenance buys
- Contradictions — C-001
