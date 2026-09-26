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

**Corpus:** 4 sources · **Wiki:** 10 entities · 23 concepts · 3 topics · 1 answer
**Health:** 0 lint findings · **Search:** [qmd](qmd.md) indexed, 2 collections
**Conflicts:** **2 open** (C-003 belief revision, C-004 an independence claim) · 2 resolved → Contradictions

The single-source warning is gone, and something better replaced it: the corpus now
contains a primary text that **corrects** the document the whole system is built on.
That was the first real test of AGENTS.md §5 — it produced two registered
contradictions rather than a silent overwrite, and both were ruled on by the owner the
same day. Five pages carried `status: contested` while the rulings were pending; none
do now.

## What the corpus is about

Three topics: [Augmenting Human Intellect](augmenting-human-intellect.md) (root), [Personal Knowledge Management](personal-knowledge-management.md)
and [Agent Memory](agent-memory.md). Four sources — three primary and one anonymous secondary account that
descends from two of them without knowing they existed.

**The newest source is a mirror.** [Hindsight is 20/20: Building Agent Memory that Retains, Recalls, and Reflects](Sources.md) describes a production
agent-memory system that converges with this vault on its deepest principle — provenance
must be structural, not incidental ([Epistemic Separation](epistemic-separation.md)) — and diverges sharply on the
one question that matters most: whether belief revision should be automatic or
human-adjudicated ([Opinion Reinforcement](opinion-reinforcement.md), C-003). It also does three things we don't:
measures itself, reasons over time, and builds a typed causal graph automatically. The
comparison is filed as the vault's first answer page,
[How does this vault compare with Hindsight?](ans-2026-09-26-vault-vs-hindsight.md).

**The reframe, from Engelbart.** The unit of analysis is not the person or the tool but
[H-LAM/T](h-lam-t.md) — *Human using Language, Artifacts, Methodology, in which he is Trained*.
Effectiveness is a property of that system, so a vault that changes the artifact without
changing the method changes little. That is why the schema file exists: it *is* the M.
Intelligence on this account is **organization**, not substance ([Synergism](synergism.md)), and what
gets amplified is the whole system rather than its human component
([Intelligence Amplification](intelligence-amplification.md)).

**The critique this vault has not answered.** Concept structures are multiply-connected
networks; every medium we write in is a serial string. Engelbart: projecting the first into
the second means *"the human memory and visualization has to hold and picture the links and
relationships."* A markdown wiki is exactly that projection. Hubs, backlinks, graph view and
[Typed Links](typed-links.md) are compensation, not a solution. → [N-Dimensional Projection Problem](n-dimensional-projection-problem.md)

**The mechanism, agreed by all three.** Knowledge is stored once and connected many times,
and the connections are the valuable artifact. Bush states it as engineering — *"The process
of tying two items together is the important thing"* — and his objection to hierarchy is
structural: filed in one place, an item forces you to *"emerge from the system and re-enter
on a new path"* for every new thread. [Associative Indexing](associative-indexing.md) is what `wikilinks`
implement.

**Maintenance burden now has first-person evidence.** Engelbart ran an edge-notched card
system for eight years — kernels of thought, one deck per problem, source and page on every
card — and reports why it failed: he *"just didn't have the means to keep track of all of the
kernel statements and the various relationships between them"* by means easy enough to leave
capacity for the actual thinking. He also turns the diagnosis into a **threshold**: below
some convenience level a system is not slow but *"unusable."* And his conclusion is the
warrant for having a schema at all — even if the equipment *"appeared on the market
tomorrow, a good deal of empirical research would be needed to develop a methodology."*
→ [Maintenance Burden](maintenance-burden.md)

**The division of labor, corroborated.** This is the strongest thing in the corpus,
because two independent sources draw the same line. Bush: *"For mature thought there is
no mechanical substitute. But creative thought and essentially repetitive thought are
very different things."* The creative part is *"the selection of the data and the process
to be employed"*; the rest *"is a fit matter to be relegated to the machines."* The
pattern doc says: human curates and directs, LLM does the bookkeeping. Same split, 81
years apart. → [Repetitive vs Creative Thought](repetitive-vs-creative-thought.md)

**The disagreement that remains.** Bush's bottleneck is **selection** — *"The prime action
of use is selection, and here we are halting indeed"* — with Mendel's genetics *"lost to the
world for a generation"* as the paradigm failure. The pattern doc's is **consistency**.
Engelbart's is **structure**: whether the notation lets you think at all. Three different
problems, one corpus, and no source addressing all three. A vault that only links pages
doesn't help you find things; one that only searches doesn't accumulate.
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

**How firmly to hold this.** Better than a day ago. Three sources, two of them primary, one
reporting lived experience rather than a proposal. But: no experiment is reported anywhere
in the corpus; Engelbart's most vivid material (§III.B) is **fiction** by his own
declaration, and its *"ten times as effective"* figure is invented illustration, not data;
[Typed Links](typed-links.md) was adopted on qualitative evidence with no numbers attached; and the vault
satisfies neither of Engelbart's two minimal measurement requirements — knowing *when*
something improved, and being able to *compare* two competing changes. The pattern doc's
self-serving error also stands as a warning about its whole class: confident, plausible,
uncorroborated.

## How to navigate

- **Index** — the full catalog, grouped by type, with a status board
- **[Augmenting Human Intellect](augmenting-human-intellect.md)** — the root hub; the best entry point
- **[Personal Knowledge Management](personal-knowledge-management.md)** — the knowledge-base sub-hub
- **[Agent Memory](agent-memory.md)** — persistent memory for agents; where Hindsight sits
- **[How does this vault compare with Hindsight?](ans-2026-09-26-vault-vs-hindsight.md)** — the first filed answer
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
