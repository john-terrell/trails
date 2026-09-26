---
type: concept
title: LLM Wiki Pattern
aliases: [LLM Wiki, the wiki pattern, compiled knowledge base]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/pkm, concept/llm-agents]
confidence: high
sources: 3
---

# LLM Wiki Pattern

A method for building a personal knowledge base in which an LLM agent incrementally
compiles raw sources into a persistent, interlinked markdown wiki and maintains that
wiki as new material arrives — rather than retrieving fragments from the raw sources
at query time. The human curates sources and asks questions; the LLM does all the
summarizing, cross-referencing, filing, and bookkeeping.

## Definition

Three layers, strictly separated
([LLM Wiki](Sources.md)):

| Layer | Contents | Ownership |
|---|---|---|
| **Raw sources** | Articles, papers, images, data. Immutable — the source of truth. | Human curates; LLM reads only |
| **The wiki** | LLM-generated markdown: source summaries, entity pages, concept pages, topic hubs, comparisons, synthesis | **LLM exclusively** |
| **The schema** | A config file (`AGENTS.md`, `CLAUDE.md`) defining structure, conventions, and workflows | Co-evolved by both |

The schema is what distinguishes this from "an LLM with a folder of notes." It is
"what makes the LLM a disciplined wiki maintainer rather than a generic chatbot."

**Not** a RAG system, and not a note-taking app the human maintains. The defining
property is that the wiki is a *compiled artifact*: synthesis happens once at ingest
time and is kept current, not re-derived per question. See
[Retrieval-Augmented Generation](retrieval-augmented-generation.md) for the contrast.

## How it works

Three operations
([LLM Wiki](Sources.md)):

**Ingest.** A source is dropped into the raw collection. The LLM reads it, discusses
takeaways with the human, writes a summary page, updates the index, updates the
relevant entity and concept pages across the wiki, and appends to the log. "A single
source might touch 10-15 wiki pages." Can be done one-at-a-time with supervision or
batched with less.

**Query.** The LLM reads `index.md` to find relevant pages, drills into them, and
synthesizes an answer with citations. Output form varies: markdown page, comparison
table, [Marp](marp.md) deck, matplotlib chart, Obsidian canvas. Critically, good answers get
**filed back into the wiki** so explorations compound alongside ingested sources.

**Lint.** Periodic health check for contradictions between pages, stale claims
superseded by newer sources, orphan pages with no inbound links, important concepts
mentioned but lacking their own page, missing cross-references, and data gaps a web
search could fill.

Two navigation files carry the structure: **`index.md`**, a content-oriented catalog
of every page with a one-line summary, organized by category; and **`log.md`**, an
append-only chronological record. Consistent log entry prefixes make the history
parseable with plain unix tools — `grep "^## \[" log.md | tail -5`.

## Why it matters

It converts the economics of knowledge maintenance. The claim is that wikis fail for
a specific reason — [Maintenance Burden](maintenance-burden.md) grows faster than value — and that LLMs
remove exactly that cost:

> LLMs don't get bored, don't forget to update a cross-reference, and can touch 15
> files in one pass. The wiki stays maintained because the cost of maintenance is
> near zero.

The consequence is [Knowledge Compounding](knowledge-compounding.md): cross-references, flagged
contradictions, and an evolving synthesis are already present at query time instead
of being reconstructed.

The working setup is deliberately side-by-side: agent on one side, [Obsidian](obsidian.md) on
the other, human watching edits land and browsing the graph view. "Obsidian is the
IDE; the LLM is the programmer; the wiki is the codebase."

## Evidence

Two sources now, and they pull in different directions. The founding document is a
proposal rather than a study; the primary text corroborates its mechanism and undercuts
its history.

- **The division of labor, independently anticipated.** The strongest support the
  pattern has. [Vannevar Bush](vannevar-bush.md) drew the same line 81 years earlier: *"For mature
  thought there is no mechanical substitute. But creative thought and essentially
  repetitive thought are very different things"* (§3), with the creative part *"concerned
  only with the selection of the data and the process to be employed, and the
  manipulation thereafter … a fit matter to be relegated to the machines"* (§4). Two
  proposals that far apart agreeing on where the line falls is real corroboration.
  → [Repetitive vs Creative Thought](repetitive-vs-creative-thought.md)
- **The mechanism is genuinely Bush's.** [Associative Indexing](associative-indexing.md) — many-to-many links,
  named replayable paths, an item belonging to numerous trails — is what wikilinks
  implement, and Bush's §6 objection to hierarchy (*"It can be in only one place"*) is a
  better argument for links-over-folders than the pattern doc itself offers.
  → [Memex](memex.md)
- **The lineage claim, corrected.** [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) says Bush's
  vision was *"private, actively curated"* and that *"the part he couldn't solve was who
  does the maintenance."* The primary text contradicts both: trails are shared, gifted,
  and inherited (§7–8), and Bush proposes *"a new profession of
  [trail blazers](trail-blazer.md)"* (§8). → Contradictions C-001, C-002
- **They solve different problems.** Bush's bottleneck is **selection** across a
  literature too large to read; the pattern's is **consistency** across a personal
  corpus. The descent is real at the level of mechanism and mistaken at the level of
  purpose. → [Growing Mountain of Research](growing-mountain-of-research.md)
- **The [Tolkien Gateway](tolkien-gateway.md) existence proof.** Fan wikis demonstrate that dense
  interlinked knowledge bases do get built and maintained — by communities of
  volunteers over years. The pattern replaces the community with one agent. Note this
  is a *third* strategy (distribution), not the pattern's (automation), and it is the
  one with the best track record. → [Maintenance Burden](maintenance-burden.md)
- **This vault.** A first-hand, running instance. Its Log is the evidence trail —
  and ingest #2 is the first case of a source *revising* existing pages rather than
  merely adding to them, which is the mechanism the pattern claims and had not yet been
  exercised.

## Criticisms and limits

- **Its history is wrong in a way that flatters it.** The lineage claim depends on Bush
  having left the maintenance question open. He did not — he staffed it
  ([Trail Blazer](trail-blazer.md)). The pattern is more novel than it claims to be, which is a better
  position than the one it argues for, but the argument as written does not survive the
  primary text. → Contradictions C-001
- **It addresses one bottleneck and ignores the other.** Nothing in the pattern helps
  you *find* something across a corpus too large to browse — Bush's actual problem. This
  vault compensates by running [qmd](qmd.md) over the compiled pages, which is an addition to
  the pattern rather than an instance of it. → [Growing Mountain of Research](growing-mountain-of-research.md)
- **Unmeasured scale claims.** `index.md` is asserted to work "surprisingly well at
  moderate scale (~100 sources, ~hundreds of pages)" with no measurement offered.
  Where exactly it breaks, and how it breaks, is unknown.
- **Anonymous provenance.** No author, no date, no prior deployments cited. Treat the
  design as plausible and unvalidated rather than established.
- **Compile-time cost is real, just relocated.** Integration work moves from query
  time to ingest time. A corpus that is mostly *searched* rather than *synthesized*
  may not repay it — plain [Retrieval-Augmented Generation](retrieval-augmented-generation.md) would be cheaper.
- **The LLM owns the wiki, so errors compound too.** A wrong synthesis, once written,
  is cited by every page that follows. The pattern mitigates this with citations,
  contradiction flagging, and lint passes, but not with any independent verification
  step.
- **Team operation is sketched, not designed.** "Possibly with humans in the loop
  reviewing updates" is the entire treatment of multi-writer governance.
- **Tooling drift.** The doc names [qmd](qmd.md), [Marp](marp.md), [Dataview](dataview.md), and
  [Obsidian Web Clipper](obsidian-web-clipper.md). All are optional and modular; none is load-bearing.

## Instances and applications

The doc lists applicable contexts: personal self-tracking (goals, health,
psychology), research deep-dives over weeks or months, reading a book chapter by
chapter, business/team wikis fed by Slack threads and meeting transcripts, and
"competitive analysis, due diligence, trip planning, course notes, hobby deep-dives."

- **This vault** — mixed/general second brain, instantiated 2026-09-26. Schema at
  AGENTS.md.

## Open questions

- What actually happens to `index.md` navigation past ~100 sources?
- Does collaborative ingest (read → discuss → write) stay worth its overhead at volume,
  or does batch mode win?
- How should a team review LLM wiki edits without recreating the maintenance burden
  the pattern exists to remove?

→ tracked in Open Questions

## Sources

- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — the founding document; its Bush passage is
  **contradicted** by the primary text
- [As We May Think](Sources.md) — primary; corroborates the mechanism and the
  division of labor, contradicts the lineage claim

## Relations

- **derives-from** [Memex](memex.md) — the mechanism is Bush's; the purpose is not
- **contrasts** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — compile once vs retrieve per query
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
