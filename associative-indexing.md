---
type: concept
title: Associative Indexing
aliases: [associative indexing, associative trails, trails, trail]
created: 2026-09-26
updated: 2026-09-26
status: growing
tags: [concept/pkm, concept/information-retrieval, concept/history]
confidence: high
sources: 1
---

# Associative Indexing

The mechanism at the center of [Vannevar Bush](vannevar-bush.md)'s [Memex](memex.md): instead of filing an item
in one place in a hierarchy, you **tie it to other items**, and the ties become
navigable paths — *trails* — that can be named, replayed, branched, shared, and
inherited. Bush calls it *"the essential feature of the memex"* and is emphatic about
what actually matters: *"The process of tying two items together is the important thing"*
([As We May Think](Sources.md), §7).

## Definition

Bush's formulation (§7):

> associative indexing, the basic idea of which is a provision whereby any item may be
> caused at will to select immediately and automatically another.

Two properties distinguish it from an index:

1. **Many-to-many.** *"any item can be joined into numerous trails."* An item is not
   located *in* a structure; it is *referenced by* many.
2. **The path is the artifact.** A trail is named, stored in a code book, and replayable
   — *"they can be reviewed in turn, rapidly or slowly, by deflecting a lever … It is
   exactly as though the physical items had been gathered together to form a new book."*
   The sequence of hops carries meaning that none of the individual items does.

## What it replaces, and why

Bush's target is hierarchical classification, and his objection is structural rather
than aesthetic (§6):

> Our ineptitude in getting at the record is largely caused by the artificiality of
> systems of indexing. When data of any sort are placed in storage, they are filed
> alphabetically or numerically, and information is found (when it is) by tracing it down
> from subclass to subclass. It can be in only one place, unless duplicates are used; one
> has to have rules as to which path will locate it, and the rules are cumbersome. Having
> found one item, moreover, one has to emerge from the system and re-enter on a new path.

Three distinct failures: **single placement** (or costly duplication), **cumbersome
placement rules** (you must know the taxonomy before you can file), and **no lateral
movement** (every new thread means returning to the root). His alternative is
biological: *"The human mind does not work that way. It operates by association. With one
item in its grasp, it snaps instantly to the next that is suggested by the association of
thoughts, in accordance with some intricate web of trails carried by the cells of the
brain."*

The claim is not that machines can match the mind — Bush is careful: *"Man cannot hope
fully to duplicate this mental process artificially, but he certainly ought to be able to
learn from it"* — but that machines win on a different axis: *"it should be possible to
beat the mind decisively in regard to the permanence and clarity of the items
resurrected from storage."* Persistence, not speed. → [Knowledge Compounding](knowledge-compounding.md)

## How it maps onto this vault

Associative indexing is what `wikilinks` implement, and the mapping is close enough
to be worth stating precisely (AGENTS.md §6.3).

| Bush's memex | This vault |
|---|---|
| Item | A wiki page |
| Tying two items together | `a link` in prose, at the point where the connection is meaningful |
| Code space + photocell dots | Obsidian's backlink index |
| Named trail | A topic hub, or a filed answer page |
| Replaying a trail | Following links from a hub, or graph view |
| Item in numerous trails | One page linked from many hubs |
| Trail gifted to a friend | git push to a shared remote |
| Ready-made encyclopedias with trails | Nothing yet — see "Open questions" |

**The important consequence is negative.** If folders are the *"artificiality of systems
of indexing"* Bush objected to, then `wiki/entities/`, `wiki/concepts/`, `wiki/topics/`
are filing convenience and nothing more. A page's meaning is carried by its links, not
by its directory. Two operational rules follow, and both are already in the schema:
prefer updating an existing page over creating a near-duplicate in a different folder
(§2), and link aggressively because links are the structure (§3.6).

It also implies the folder taxonomy should stay **shallow and boring**. Deep nesting
reintroduces exactly the problem — single placement plus cumbersome rules.

## Why it matters

It is the mechanism that makes [Knowledge Compounding](knowledge-compounding.md) possible. A corpus of unlinked
summaries grows linearly: n sources, n files. A corpus where each new source is *tied
into* existing items grows combinatorially in reachable structure, and the ties are the
part that survives. Bush puts it as permanence: *"And his trails do not fade"* (§7).

It is also the strongest point of agreement between Bush and
[LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md), and the reason that document's claim of descent is
legitimate at the level of mechanism even where it misdescribes Bush's purpose. See
[Memex](memex.md) §"Divergence".

## Criticisms and limits

- **Bush never addresses trail quality.** No staleness, no error, no conflicting trails.
  A trail is assumed useful because someone built it deliberately. When an agent builds
  links at machine speed, wrong associations propagate as readily as right ones — which
  is what the Contradictions register and the lint pass (§9) are for, and neither
  exists in Bush's design.
- **Trails encode one reader's judgment.** Bush's bow-and-arrow trail is useful to *him*
  and to the friend he gives it to. Generalizing that to a shared encyclopedia assumes
  the trail-maker's framing transfers, which is the same assumption a wiki's editorial
  voice makes.
- **Many-to-many has a cost the essay skips.** Every item joinable to many trails means
  no canonical location, which makes deduplication and merge decisions harder. This
  vault's §10 merge workflow is that cost, made concrete.
- **Selection still has to happen.** Trails help you move *after* you have an entry
  point. Bush's own bottleneck — *"The prime action of use is selection"* (§5) — is
  partly solved by trails and partly not; finding the *first* item in a large corpus is
  a search problem, which is why [qmd](qmd.md) exists alongside the link graph.

## Sources

- [As We May Think](Sources.md) — primary; §6 states the objection to indexing, §7
  specifies the mechanism and gives the bow-and-arrow worked example

## See also

- [Memex](memex.md) — the device this mechanism belongs to
- [Trail Blazer](trail-blazer.md) — who builds trails, and who pays them
- [Knowledge Compounding](knowledge-compounding.md) — what permanent trails enable
- [Growing Mountain of Research](growing-mountain-of-research.md) — the problem being solved
- [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — the alternative answer to selection
- [Obsidian](obsidian.md) — the tool implementing it here
