---
type: topic
title: Personal Knowledge Management
aliases: [PKM, knowledge management, second brain]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [topic, pkm]
confidence: medium
sources: 3
---

# Personal Knowledge Management

The domain this vault belongs to: how one person accumulates, organizes, and retrieves
knowledge over long periods. **A sub-hub of [Augmenting Human Intellect](augmenting-human-intellect.md)** — PKM is the
record-keeping and retrieval corner of a broader question about tools, language, method
and training.

The corpus holds three sources: two primary texts 17 years apart, and one anonymous
secondary account that descends from both without knowing the second.
[Vannevar Bush](vannevar-bush.md)'s bottleneck is **selection** across a literature too large to read;
[Douglas Engelbart](douglas-engelbart.md) reframes the whole thing as a systems problem and supplies the first
empirical account of a personal knowledge system failing; the
[pattern doc](Sources.md)'s bottleneck is **consistency**. The most
useful thing the third source did was correct the first one's history — see
Contradictions.

## Core concepts

- [LLM Wiki Pattern](llm-wiki-pattern.md) — compile sources into a maintained wiki instead of retrieving fragments per query *(its history was wrong; corrected by the primary text)*
- [Associative Indexing](associative-indexing.md) — many-to-many links and named, replayable trails; the shared mechanism
- [Maintenance Burden](maintenance-burden.md) — the bookkeeping cost that makes humans abandon wikis *(C-001 resolved)*
- [Growing Mountain of Research](growing-mountain-of-research.md) — Bush's selection problem; the bottleneck the pattern does not address
- [Knowledge Compounding](knowledge-compounding.md) — each source and answer raising the value of what is already filed
- [Repetitive vs Creative Thought](repetitive-vs-creative-thought.md) — Bush's criterion for what to delegate; the pattern's division of labor, 81 years early
- [Trail Blazer](trail-blazer.md) — Bush's proposed profession; the hinge of C-001
- [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — the dominant alternative, and the contrast case
- [Memex](memex.md) — the 1945 device that specified all of this *(C-002 resolved)*

## Key entities

- [Vannevar Bush](vannevar-bush.md) — author of the primary text; Director of the OSRD in 1945
- [Obsidian](obsidian.md) — the reading surface; wikilinks implement associative indexing
- [qmd](qmd.md) — local hybrid search over compiled pages (installed here)
- [Obsidian Web Clipper](obsidian-web-clipper.md) — source acquisition into `raw/clippings/`
- [NotebookLM](notebooklm.md) — cited as an instance of the RAG approach
- [Tolkien Gateway](tolkien-gateway.md) — existence proof that dense wikis survive, by *distributing* the labor
- [Marp](marp.md), [Dataview](dataview.md) — optional output and view layers

## Sources

- [Augmenting Human Intellect: A Conceptual Framework](Sources.md) (1962-10, **primary**) — Engelbart, SRI
  AFOSR-3223, 144 pages. The framework, the Bush critique, and a first-person account of
  a note-card system defeated by its own bookkeeping. **§III.B is fiction.**
- [As We May Think](Sources.md) (1945-07, **primary**) — Bush, *The Atlantic Monthly*.
  Specifies the memex and associative indexing; identifies selection as the bottleneck;
  proposes trail blazers. Text corrected 2026-09-26 against the Engelbart witness.
- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) (2026-09-26, **secondary, anonymous**) — the vault's
  founding document. Three layers, three operations, automation as the answer to
  maintenance. Its Bush passage is contradicted by both primary texts.

## Analyses

*None filed yet. The obvious first one: **Bush's memex vs. the LLM wiki, as two answers
to two different problems** — a comparison table exists in draft across [Memex](memex.md) and
[LLM Wiki Pattern](llm-wiki-pattern.md) and could be promoted to a filed answer.*

## Current understanding

**The mechanism is settled and old.** Both sources converge on the same design: knowledge
is stored once and connected many times, and the connections are the valuable artifact.
Bush states it as engineering — *"The process of tying two items together is the
important thing"* (§7) — and his objection to hierarchy is structural, not stylistic.
Filed alphabetically or numerically, an item *"can be in only one place, unless
duplicates are used"*, and *"having found one item, moreover, one has to emerge from the
system and re-enter on a new path"* (§6). The pattern doc reaches the same place from the
other direction and never states the argument as well. [Associative Indexing](associative-indexing.md) is what
`wikilinks` implement, and this vault's folders are filing convenience rather than
structure.

**The division of labor is corroborated, and this is the strongest thing in the corpus.**
Bush: *"For mature thought there is no mechanical substitute. But creative thought and
essentially repetitive thought are very different things"* (§3); the creative element is
*"concerned only with the selection of the data and the process to be employed, and the
manipulation thereafter is repetitive in nature and hence a fit matter to be relegated to
the machines"* (§4). The pattern doc assigns the human to curation and direction and the
LLM to bookkeeping. Two proposals 81 years apart drawing the line in the same place is
real evidence — and it is why this vault's collaborative ingest mode (discuss before
writing) is a correct allocation rather than a preference. See
[Repetitive vs Creative Thought](repetitive-vs-creative-thought.md).

**They disagree about the problem, and the pattern doc doesn't notice.** Bush's
bottleneck is selection: *"The prime action of use is selection, and here we are halting
indeed"* (§5), with Mendel's genetics *"lost to the world for a generation"* as the
paradigm failure (§1). The pattern doc's bottleneck is consistency: wikis die because
[Maintenance Burden](maintenance-burden.md) outruns value. Neither is wrong, and they are not the same
problem. A vault that only links pages does not help you find things; a vault that only
searches does not accumulate anything. → [Growing Mountain of Research](growing-mountain-of-research.md)

**The pattern doc's history is wrong, in a way that flatters it.** It claims Bush
*"couldn't solve"* who does the maintenance. Bush proposed *"a new profession of
[trail blazers](trail-blazer.md)"* (§8), and made the trails social — gifted, published
inside ready-made encyclopedias, inherited by disciples. Both misdescriptions are
registered as Contradictions C-001 and C-002. The consequence is that there are
**three** answers to maintenance burden in this corpus, not one: staff it (Bush),
distribute it ([Tolkien Gateway](tolkien-gateway.md)), automate it (the pattern). Distribution has by far
the best track record, automation the least, and the pattern doc never mentions the
other two as alternatives.

**Bush's economics argument is better than the pattern doc's.** Leibnitz's calculating
machine *"could not then come into use. The economics of the situation were against it"*;
Babbage's engine, *"his idea was sound enough, but construction and maintenance costs
were then too heavy"*; and now *"the world has arrived at an age of cheap complex devices
of great reliability; and something is bound to come of it"* (§1). Substitute
*maintenance* for *construction* and this is the pattern doc's whole thesis — but stated
as a general law about stalled ideas rather than asserted about one. It also implies a
test nobody has run: if the bottleneck was cost, the value of automating depends on how
expensive the manual version actually was. That is measurable.

**How firmly to hold this.** Better than yesterday, still loosely. The primary source is
genuinely strong and the corroborated division of labor is now two-source. But the
corpus still contains no empirical account of an LLM-maintained wiki, no reception
history for Bush, no independent treatment of RAG, and no measurement of anything. And
the pattern doc's self-serving error is a warning about the class of source it belongs
to: confident, plausible, uncorroborated.

## Tensions and open questions

- **C-001 and C-002 were ruled on 2026-09-26**, both for the primary text, and C-002's
  normative half has since been **acted on**: trails are now published to a public repo
  (AGENTS §16). Engelbart independently corroborates the finding, reading Bush's trail
  gifting and *"wholly new forms of encyclopedia"* as *"changes in the ways in which people
  can cooperate intellectually."* → Contradictions
- **Is the agent a trail blazer?** It builds trails, but under direction rather than
  from delight, for one reader rather than the common record. Whether that distinction
  changes how much judgment to delegate is unresolved. → [Trail Blazer](trail-blazer.md)
- **Nobody has measured the alternative.** The corpus still has no comparison of
  wiki-plus-search against plain notes plus [RAG](retrieval-augmented-generation.md), and
  no measurement of ingest cost versus query savings.
- **Bush never considers a wrong trail.** No staleness, no error, no conflicting trails.
  The pattern doc's contradiction register addresses a gap Bush left — and that gap is
  *wider* when an agent builds links at machine speed.

## Relations

- **part-of** [Augmenting Human Intellect](augmenting-human-intellect.md)
- **derives-from** [Augmenting Human Intellect: A Conceptual Framework](Sources.md)
- **derives-from** [As We May Think](Sources.md)
- **derives-from** [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md)
- **specializes** [H-LAM/T](h-lam-t.md) — the L and A components applied to a personal record
