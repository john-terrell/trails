---
type: concept
title: Memex
aliases: [memex, memory extender, mechanized private file]
created: 2026-09-26
updated: 2026-09-26
status: stable
tags: [concept/pkm, concept/history]
confidence: high
sources: 3
---

# Memex

A desk-sized device proposed by [Vannevar Bush](vannevar-bush.md) in 1945 in which an individual stores
all his books, records, and communications on microfilm and consults them by following
**associative trails** — named, permanent, shareable paths between items — instead of by
hierarchical index. Bush's own coinage, offered casually: *"It needs a name, and to coin
one at random, 'memex' will do"* ([As We May Think](Sources.md), §6).
It is the direct ancestor of [LLM Wiki Pattern](llm-wiki-pattern.md), and the primary text shows the
relationship is closer in mechanism and looser in purpose than the pattern doc claims.

> [!note] Corrected by primary text — C-001 and C-002 **resolved** 2026-09-26
> [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) describes the memex as *"private, actively
> curated"* and claims Bush *"couldn't solve"* who does the maintenance. The primary text
> contradicts both: trails are explicitly shared and inherited (§7–8), and Bush proposes
> a [profession of trail blazers](trail-blazer.md) (§8). **The owner ruled for the primary
> text on both.** This page follows Bush. Register: Contradictions C-001, C-002.

## Definition

Bush's full definition, verbatim (§6):

> Consider a future device for individual use, which is a sort of mechanized private
> file and library. … A memex is a device in which an individual stores all his books,
> records, and communications, and which is mechanized so that it may be consulted with
> exceeding speed and flexibility. It is an enlarged intimate supplement to his memory.

Three things in that definition are load-bearing and easy to miss. It is for
**individual** use. It is a **supplement to memory**, not a replacement for it — the goal
is offloading, so that one may *"reacquire the privilege of forgetting the manifold
things he does not need to have immediately at hand, with some assurance that he can find
them again if they prove important"* (§8). And it is defined by how it is **consulted**,
not by how much it holds.

## The problem it answers

Not storage. Bush's diagnosis is that recording has already outrun consulting (§5):

> Thus far we seem to be worse off than before — for we can enormously extend the
> record; yet even in its present bulk we can hardly consult it. … The prime action of
> use is selection, and here we are halting indeed.

Selection today is *"a stone adze in the hands of a cabinetmaker"* (§5). See
[Growing Mountain of Research](growing-mountain-of-research.md) for the fuller statement of the problem, and note that
this is a **retrieval** problem, not a consistency problem — which is where Bush and
[LLM Wiki Pattern](llm-wiki-pattern.md) part company. See "Divergence" below.

## Specification

Bush is unusually concrete; the memex is an engineering sketch, not a metaphor
(§6–7, [As We May Think](Sources.md)).

| Component | Bush's design |
|---|---|
| **Form** | A desk. *"Slanting translucent screens"* for projection, a keyboard, buttons and levers. *"Otherwise it looks like an ordinary desk."* |
| **Storage** | Microfilm, assumed linear reduction of 100 — a factor of 10,000 in bulk |
| **Capacity** | Effectively unbounded: *"if the user inserted 5000 pages of material a day it would take him hundreds of years to fill the repository, so he can be profligate and enter material freely"* |
| **Acquisition** | Most contents *"purchased on microfilm ready for insertion"* — books, periodicals, newspapers, business correspondence |
| **Direct entry** | A transparent platen on top; longhand notes, photographs, memoranda are photographed onto the next blank film space by dry photography, at the throw of a lever |
| **Retrieval** | Mnemonic codes tapped on the keyboard project an item onto a viewing position; a code book for the rest |
| **Paging** | Levers step 1, 10, or 100 pages at a time, forward or backward |
| **Side-by-side** | Multiple projection positions, so *"he can leave one item in position while he calls up another"* |
| **Annotation** | Marginal notes by dry photography, possibly by a stylus scheme like the telautograph |
| **Trails** | See [Associative Indexing](associative-indexing.md) |

## How trails work

The mechanism, exactly as Bush describes it (§7). Two items are projected onto adjacent
viewing positions. Each has blank code spaces at the bottom; a pointer is set to one
space on each. The user taps a single key and *"the items are permanently joined."*
Invisible to the reader but present in the code space is a set of dots for photocell
reading, whose positions encode the index number of the *other* item — so tapping the
button beneath a code space recalls its partner instantly.

A trail is named, entered in the code book, and thereafter replayable: *"when numerous
items have been thus joined together to form a trail, they can be reviewed in turn,
rapidly or slowly, by deflecting a lever … It is exactly as though the physical items had
been gathered together to form a new book. It is more than this, for any item can be
joined into numerous trails."*

That last clause is the whole design. **Many-to-many.** It is what distinguishes a trail
from a folder, and it is why [Associative Indexing](associative-indexing.md) beats hierarchy: an item is no
longer confined to *"only one place."*

**Bush's worked example** (§7) is worth keeping, because it is exactly the shape of a
research session: a man studying why the short Turkish bow outperformed the English
longbow in the Crusades finds a sketchy encyclopedia article, leaves it projected, finds
a pertinent item in a history, ties the two together, and builds a trail of many items —
occasionally inserting his own comment, either into the main trail or on a side trail.
Realizing that elasticity of materials is what matters, he branches to textbooks on
elasticity and tables of physical constants, and inserts a page of his own longhand
analysis. Years later, discussing how peoples resist innovation, he recalls the trail,
photographs it out, and gives it to a friend.

## Trails are social

This is the part [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) omits, and it is not marginal (§7–8):

- Trails are **gifted**: *"he sets a reproducer in action, photographs the whole trail
  out, and passes it to his friend for insertion in his own memex, there to be linked
  into the more general trail."*
- Trails are **published**: *"Wholly new forms of encyclopedias will appear, ready-made
  with a mesh of associative trails running through them, ready to be dropped into the
  memex and there amplified."*
- Trails are **inherited**: *"The inheritance from the master becomes, not only his
  additions to the world's record, but for his disciples the entire scaffolding by which
  they were erected."*
- Professionals **accumulate** them: the lawyer has at his touch the associated opinions
  of his whole experience *"and of the experience of friends and authorities."*

So the memex is a network of private nodes with a circulation layer on top — closer to
a citation graph or a shared bookmark set than to a personal diary. → Contradictions C-002.

## Maintenance

Bush addresses it directly, in one sentence (§8):

> There is a new profession of trail blazers, those who find delight in the task of
> establishing useful trails through the enormous mass of the common record.

See [Trail Blazer](trail-blazer.md) and Contradictions C-001. His answer is a **professional class
who enjoy the work** — not automation, and not the owner doing it himself.

## Divergence from the LLM wiki pattern

Bush and [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) agree on mechanism and disagree on
bottleneck.

| | Bush (1945) | [LLM wiki](llm-wiki-pattern.md) |
|---|---|---|
| **Core problem** | Selection — finding the right item among millions | Consistency — keeping pages current and coherent |
| **Core mechanism** | [Associative trails](associative-indexing.md) | Interlinked pages |
| **Who builds the links** | The user, plus [professional trail blazers](trail-blazer.md) | An LLM agent |
| **Unit of knowledge** | The link between existing items | The rewritten page |
| **Sharing** | Explicit: trails gifted, published, inherited | Unaddressed beyond "business/team" |
| **What's new** | A device for consulting a vast record | Cheap labor for maintaining a small one |

The pattern doc's claim of descent is right about mechanism and wrong about purpose.
Bush wanted to *find* things in a literature too large to read; the LLM wiki wants to
*keep* a personal corpus coherent. A vault that does both — pages plus search — covers
ground neither proposal does alone. This one runs [qmd](qmd.md) over compiled pages for
exactly that reason.

## Engelbart's repositioning (1962)

[Douglas Engelbart](douglas-engelbart.md) read Bush closely, quoted the memex passage *"in its entirety"*, and
then argued it was a special case of something broader
([Augmenting Human Intellect](Sources.md) §III.A.2):

> The associative trails whose establishment and use within the files he describes at some
> length provide a beautiful example of a new capability in symbol structuring that derives
> from new artifact-process capability.

The critique is that trails are *"a primitive example"* of a general operation: defining a
new substructure from an arbitrary collection of existing ones, then presenting it as a
view (§III.B.5). A trail is one fixed path; the general capability is any projection on
demand. → [N-Dimensional Projection Problem](n-dimensional-projection-problem.md)

His sharper point is a **usability threshold**, and it is better argued than anything in
[LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md):

> The Memex allows a human user to do more conveniently (less energy, more quickly) what he
> could have done with relatively ordinary photographic equipment and filing systems, but
> he would have had to spend so much time in the lower-level processes of manipulation that
> his mental time constants of memory and patience would have rendered the system unusable
> in the detailed and intimate sense which Bush illustrates.

Not slow — **unusable**. And above the threshold the change is qualitative: *"Making it
easy to establish and follow the associative trails makes practical a new symbol-structuring
process whose use can make a significant difference in the concept structuring and basic
methods of work."* Convenience is a phase change, not an efficiency gain.

Engelbart also confirms the C-002 ruling independently, reading trail gifting, *"wholly new
forms of encyclopedia"*, [trail blazers](trail-blazer.md) and inheritance as *"changes in the
ways in which people can cooperate intellectually."*

## Criticisms and limits

- **Bush never considers a wrong trail.** No staleness, no error, no two trails that
  disagree. The memex assumes the record is trustworthy and the trail-builder competent.
  The [LLM Wiki Pattern](llm-wiki-pattern.md)'s contradiction register exists because
  that assumption fails — and it fails *harder* when an agent builds links at machine
  speed.
- **"Delight" is doing quiet work.** Trail blazers are people who *find delight* in the
  task. That is a strong assumption about labor supply, and it is the assumption the LLM
  removes rather than satisfies.
- **Storage was never the hard part, and Bush half-knew it.** He notes capacity is
  effectively unbounded and that *"even the modern great library is not generally
  consulted; it is nibbled by a few"* (§2). Compression gets four pages; selection gets
  two. The essay's own center of gravity is right, but its bulk is not.
- **The neural-interface coda (§8) is unearned.** Bone conduction, intercepting arm
  nerve currents, the encephalograph. Bush flags it himself as *"hardly warrant[ing]
  prediction without losing touch with reality"* — and it is the one part of the essay
  that has not aged. His extrapolations from existing mechanism largely came true; his
  single leap beyond them did not.

## Sources

- [As We May Think](Sources.md) — **primary**; §6–7 specify the device, §8 its
  consequences. Basis for the specification above. **Text corrected 2026-09-26** against
  the second witness below — eight readings, itemized in that file's frontmatter.
- [Augmenting Human Intellect: A Conceptual Framework](Sources.md) — **primary**, second witness; §III.A.1
  quotes the memex passage in full, §III.A.2 critiques and repositions it.
- [LLM Wiki — A pattern for building personal knowledge bases using LLMs](Sources.md) — names the memex as the pattern's ancestor and
  claims Bush *"couldn't solve"* maintenance; **contradicted** by both primary texts.

## Relations

- **instance-of** [Associative Indexing](associative-indexing.md) — the device that realizes the mechanism
- **derives-from** [Vannevar Bush](vannevar-bush.md) — proposed in §6–7 of his 1945 essay
- **supports** [Knowledge Compounding](knowledge-compounding.md) — trails are permanent, giftable and inheritable
- **contrasts** [Retrieval-Augmented Generation](retrieval-augmented-generation.md) — association over hierarchy; a compiled structure over retrieved fragments
- **part-of** [Personal Knowledge Management](personal-knowledge-management.md)
- **part-of** [Augmenting Human Intellect](augmenting-human-intellect.md)
- **critiques** [LLM Wiki Pattern](llm-wiki-pattern.md) — via Engelbart: trails are a primitive case, and the pattern doc misdescribes Bush
