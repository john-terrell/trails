---
type: synthesis
title: Overview
aliases: [Home, Start here]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [synthesis]
confidence: medium
sources: 2
---

# Overview

The front door to this second brain. What it currently knows, how it is organized, and
where it is heading. **This page is rewritten on each significant ingest, not appended
to.**

## What this is

A personal knowledge base maintained by an LLM agent under the rules in
AGENTS.md. Raw sources accumulate in `raw/` and are never modified.
Everything in `wiki/` is compiled from them: source summaries, entity pages, concept
pages, topic hubs, and filed answers to questions asked along the way.

It is deliberately *not* RAG. Knowledge is integrated once and kept current, instead of
being re-derived from raw fragments at every query. The founding document is
[LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md); the concept it describes is [LLM Wiki Pattern](llm-wiki-pattern.md).

## Current state

**Corpus:** 2 sources · **Wiki:** 8 entities · 9 concepts · 1 topic · 0 answers
**Health:** 0 lint findings · **Search:** [qmd](qmd.md) indexed, 2 collections
**Conflicts:** 0 open · **2 resolved** (both ruled for the primary text, 2026-09-26) → Contradictions

The single-source warning is gone, and something better replaced it: the corpus now
contains a primary text that **corrects** the document the whole system is built on.
That was the first real test of AGENTS.md §5 — it produced two registered
contradictions rather than a silent overwrite, and both were ruled on by the owner the
same day. Five pages carried `status: contested` while the rulings were pending; none
do now.

## What the corpus is about

One topic: [Personal Knowledge Management](personal-knowledge-management.md). Two sources, 81 years apart, that agree on
mechanism and disagree on purpose.

**The mechanism, agreed.** Knowledge is stored once and connected many times, and the
connections are the valuable artifact. Bush states it as engineering — *"The process of
tying two items together is the important thing"* — and his objection to hierarchy is
structural: filed in one place, an item forces you to *"emerge from the system and
re-enter on a new path"* for every new thread. [Associative Indexing](associative-indexing.md) is what
`wikilinks` implement.

**The division of labor, corroborated.** This is the strongest thing in the corpus,
because two independent sources draw the same line. Bush: *"For mature thought there is
no mechanical substitute. But creative thought and essentially repetitive thought are
very different things."* The creative part is *"the selection of the data and the process
to be employed"*; the rest *"is a fit matter to be relegated to the machines."* The
pattern doc says: human curates and directs, LLM does the bookkeeping. Same split, 81
years apart. → [Repetitive vs Creative Thought](repetitive-vs-creative-thought.md)

**The disagreement.** Bush's bottleneck is **selection** — *"The prime action of use is
selection, and here we are halting indeed"* — with Mendel's genetics *"lost to the world
for a generation"* as the paradigm failure. The pattern doc's bottleneck is
**consistency** — wikis die because [Maintenance Burden](maintenance-burden.md) outruns their value. Both
real, not the same problem, and the pattern doc doesn't notice the difference. A vault
that only links pages doesn't help you find things; one that only searches doesn't
accumulate. This one runs [qmd](qmd.md) over compiled pages for that reason.
→ [Growing Mountain of Research](growing-mountain-of-research.md)

**Where the pattern doc is wrong — now adjudicated.** It claims Bush *"couldn't solve"*
who does the maintenance. Bush proposed *"a new profession of [trail
blazers](trail-blazer.md)"* — and made his trails social, gifted and inherited rather than private. Both
misdescriptions were registered as C-001 and C-002 and **the owner ruled for the primary
text on both**. Consequence: the corpus holds **three** answers to maintenance burden,
not one. Staff it (Bush), distribute it ([Tolkien Gateway](tolkien-gateway.md)), automate it (the pattern).
Distribution has the best track record; automation, the one this vault bets on, has the
least.

**What Bush argues better.** Ideas fail on economics, not merit: Leibnitz's and Babbage's
machines were sound designs defeated by cost. *"The world has arrived at an age of cheap
complex devices of great reliability; and something is bound to come of it."* Substitute
*maintenance* for *construction* and that is the pattern doc's entire thesis — but stated
as a general law, with a testable implication nobody has run.

**How firmly to hold this.** Better than a day ago, still loosely. The primary source is
strong and the division of labor is now two-source. But there is still no empirical
account of an LLM-maintained wiki, no reception history for Bush, no independent
treatment of RAG, and no measurement of anything. The pattern doc's self-serving error is
a warning about its whole class: confident, plausible, uncorroborated.

## How to navigate

- **Index** — the full catalog, grouped by type, with a status board
- **[Personal Knowledge Management](personal-knowledge-management.md)** — the topic hub; the best entry point
- **[Glossary](glossary.md)** — terms used across the wiki
- **Contradictions** — C-001 and C-002, both resolved; kept in full so the reasoning is auditable
- **Open Questions** — what is missing, and which sources would fill it
- **Graph view** (`Cmd+G`) — hubs, bridges, and orphans at a glance
- **Log** — the timeline of everything done here

## The toolchain

[Obsidian](obsidian.md) as the reading surface (plain markdown, wikilinks, graph view, backlinks) ·
[qmd](qmd.md) for hybrid local search over compiled pages · [Obsidian Web Clipper](obsidian-web-clipper.md) to get
articles into `raw/clippings/` · git for history, pushed to a **private** GitHub remote.
[Marp](marp.md) and [Dataview](dataview.md) are documented but deliberately not installed.

## Working agreements

The human curates sources, directs the analysis, and asks the questions. The agent reads,
summarizes, cross-references, files, and maintains. Ingests are collaborative: the agent
reports takeaways and waits for direction before writing pages. Nothing lands in the wiki
without a citation, the agent's own reasoning is labeled *(inference)*, and contradictions
are registered rather than resolved by fiat — resolving them is the human's call.

**Try:** `ingest <file>` · `what do we know about X?` · `file this` · `lint` · `status` ·
`graph` — full vocabulary in AGENTS.md §11.
